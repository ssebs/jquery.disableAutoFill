# jquery.disableAutoFill
The easiest solution for disabling Google Chrome auto-fill, auto-complete functions.

----

### Why

I've spent serveral hours surfing online to look for solutions in order to disable Google Chrome auto-fill, auto-complate functions such as the screenshot below. 

![Image](https://i.imgur.com/j5Mw1ly.png)

After having tried all possible solutions I can find on Stackoverflow, howerver, they are outdated and not working. Finally I figured out that Google Chrome forces dropping the submission history while a form contains "type=password" field, so I spent 30 minutes to create this plugin to solve my problem, and yours.

### Install

```
bower install jquery.disableAutoFill
```
```
<script src="/[your_bower_path]/jquery.disableAutoFill/src/jquery.disableAutoFill.min.js"></script>
```

or

```
<script src="https://terrylinooo.github.io/jquery.disableAutoFill/assets/js/jquery.disableAutoFill.min.js"></script>
```


### Demo

https://terrylinooo.github.io/jquery.disableAutoFill/

Check out the demo page to see how it works.

### Usage

HTML
```html
<form id="login-form">
```

JS
```javascript
$('#login-form').disableAutoFill();
```

### Options

option | default | note 
---- | --- | ---
passwordFiled | - | Dom Element by ID or by ClassName, if not set, disableAutoFill will automaticlly pick up the [**type=passoword**] field.
submitButton | - | Dom Element by ID or by ClassName, if not set, disableAutoFill will automaticlly pick up the [**type=submit**] button.
debugMode | false | If true, printing form serialized data in console log instead of submitting.
randomizeInputName | true | This plugin will randomize <i><strong>input name attribute</strong></i> by default. It will restore back to original field name when submitting form. This is for preventing auto completion for all browsers (includes third-party auto-completeion extensions) not just for Google Chrome.
callback | - | To validate form fields or something you can do.

### Example

```javascript
$('#login-form').disableAutoFill({
    passwordFiled: '.password',
    callback: function() {
        return checkForm();
    }
});

function checkForm() {
    form = document.getElementById('login-form');
    if (form.password.value == '') {
        alert('Cannot leave Password field blank.');
        form.password.focus();
        return false;
    }
    if (form.username.value == '') {
        alert('Cannot leave User Id field blank.');
        form.username.focus();
        return false;
    }
    return true;
}
```

### Suggestion

This plugin may not work while the javascript render speed is slow. 
Chrome detects the **type="password"** and still assign the "remember me" to the form elements.

You can modify the input type="password" to "text", and add a class (for example: ".password")

```html
<input type="text" name="password" class="password">
```
```javascript
$(function() {
    $('.login-form').disableAutoFill({
        passwordFiled: '.password'
    });
});
```
https://jsfiddle.net/terrylinooo/hhgzbsvy/

### License

MIT

### Authors

* <a href="https://en.dictpedia.org">Terry Lin</a> (terrylinooo)




