<template>
    <div class="col-sm-8 entrance-style-filters card-white col-8 mx-auto loading-mode" id="register-state">
        <div class="spinner-border text-success position-absolute mt-10 z-100 d-none"></div>
        <div class="row w-100 pt-3">
            <div class="col-lg-4 col-sm-12">
                <div class="form-group mr-2">
                    <label for="title">عنوان: </label>
                    <input type="text" name="title" id="title" class="form-control" v-model="title">
                </div>
            </div>
            <div class="col-lg-4 col-sm-12">
                <div class="form-group mr-2">
                    <label for="to">مربوط به: </label>
                    <select class="form-control" name="to" id="to" v-model="to1">
                        <option>تست1</option>
                        <option>تست2</option>
                        <option>تست3</option>
                    </select>
                </div>
            </div>
            <div class="col-lg-4 col-sm-12">
                <div class="form-group mr-2 ml-2">
                    <label for="importance">اهمیت: </label>
                    <select class="form-control" name="to" id="importance" v-model="imp">
                        <option>زیاد</option>
                        <option>متوسط</option>
                        <option>کم</option>
                    </select>
                </div>
            </div>
        </div>
        <div class="row w-100">
            <div class="form-group mr-2 ml-2 w-100">
                <label for="text">متن: </label>
                <textarea class="form-control" name="text" id="text" rows="10" v-model="text"></textarea>
            </div>
        </div>
        <div class="row w-100">
            <div class="form-group mr-2 ml-2 w-100">
                <label for="file">فایل: </label>
                <input type="file" class="form-control" name="file" id="file">
            </div>
        </div>
        <div class="row w-100">
            <div class="form-group mr-2 ml-2 w-100">
                <button class="btn btn-bg-shadow w-100" @click="onSubmit">ثبت</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'add-case-main',
        data() {
            return {
                title: '',
                to1: '',
                imp: '',
                text: '',
            }
        },
        methods: {
            onSubmit(){
                var vm = this;
                $.post('/api/student-add-case.json', {
                    title: vm.title,
                    to: vm.to1,
                    important: vm.imp,
                    text: vm.text,
                }, function (data) {
                    if(data.status){
                        vm.title = '';
                        vm.to1 = '';
                        vm.imp = '';
                        vm.text = '';
                        alert(data.message);
                    }
                })
            }
        }
    }
</script>