---
title: "Problem in javascript?"
date: 2011-05-29
forum: Programming Talk
---

### Post by scott_tiger on 2011-05-29
<html>
<head><script="text/javascript">
function isNumberKey(evt)
        {
         var charCode = (evt.which) ? evt.which : event.keyCode
         if (charCode > 31 && (charCode < 48 || charCode > 57)){
                alert("Please fill only digits");
            return false;
         return true;
        }
}
</script></head>
<body>
<form>
<label>Phone<input type="text" name="phone" id="phone" size="10" onKeyPress="return isNumberKey(event)" MAXLENGTH="10"></label>
<input type="submit" value="Submit!" />
</form>
</body>
</html>

I am using above script to check whether the input in the field is DIGIT or not..
If it is not a digit ,It prompts to "fill digit"..

But when I am submitting the form having Phone **field empty the** form gets submitted..

Plz guide me how to alert user when the Phone field is empty during form submission

---

### Post by lavinog on 2011-05-29
In the future, please use code tags so that it is readable.

You can try something like this:
[php]
<html>
<head>
<script type="text/javascript">
function isNumberKey(evt)
{
    var charCode = (evt.which) ? evt.which : event.keyCode
    if (charCode > 31 && (charCode < 48 || charCode > 57)){
        alert("Please fill only digits");
        return false;
        return true;
    }
}

function isEmpty()
{
    var phone = document.getElementById("phone").value;
    if (phone.length==0){
        alert("Empty Field");
    }
}

</script>

</head>
<body>

<form>
<label>Phone<input type="text" name="phone" id="phone" size="10" onKeyPress="return isNumberKey(event)" MAXLENGTH="10" ></label>
<input type="submit" value="Submit!" onclick="isEmpty()" />
</form>

</body>
</html>
[/php]

Keep in mind that I am not that great with javascript

---

### Post by Petrolea on 2011-05-29
> **scott_tiger said:**
> <html>
<head><script="text/javascript">
function isNumberKey(evt)
        {
         var charCode = (evt.which) ? evt.which : event.keyCode
         if (charCode > 31 && (charCode < 48 || charCode > 57)){
                alert("Please fill only digits");
            return false;
         return true;
        }
}
</script></head>
<body>
<form>
<label>Phone<input type="text" name="phone" id="phone" size="10" onKeyPress="return isNumberKey(event)" MAXLENGTH="10"></label>
<input type="submit" value="Submit!" />
</form>
</body>
</html>

I am using above script to check whether the input in the field is DIGIT or not..
If it is not a digit ,It prompts to "fill digit"..

But when I am submitting the form having Phone **field empty the** form gets submitted..

Plz guide me how to alert user when the Phone field is empty during form submission

I'm not great in JavaScript but is there maybe a ';' missing?
```
var charCode = (evt.which) ? evt.which : event.keyCode
```

---

