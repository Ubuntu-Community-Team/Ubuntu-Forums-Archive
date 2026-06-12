---
title: "Concatenating field id with string in javascript"
date: 2010-10-26
forum: Programming Talk
---

### Post by sarin_cv on 2010-10-26
```

<script language="Javascript">

function whichRadio(obj)
{
    alert(obj.id);

    for (i=0;i<document.f1.radioTest.length;i++)
    {
        if (document.f1.radioTest[i].checked)
        {
            alert(document.f1.radioTest[i].value);
        }
    }
    return true;
}

</script>

<form name=f1>
<P>
<td>
<input type="radio" name="radioTest" value="Y" id="radioTest" onClick="whichRadio(this); "> Yes
<input type="radio" name="radioTest" value="N" id="radioTest" onClick="whichRadio(this); "> No </td>


<P>
</form>
<div id=itext>Which one will you choose?</div>

```


this is a simple functtion for a radio button click. I want to generalize this function so that in whichRadio function, I have to use obj.id instead of radioTest. Please help.

---

### Post by gmargo on 2010-10-26
I can't see why you would use obj.id since you have obj.  In any case, to search the block of radio buttons you have to search by name, since searching by id will only give the first matching element, not all of them.

Something like this might work for you:
```

function whichRadio(obj)
{
    //alert(obj.id);

    if (obj.type == "radio")
    {
        // Find all elements of same name
        var radios = document.getElementsByName(obj.name);
        for (i=0; i < radios.length; i++)
        {
            var radio = radios[i];
            if (radio.checked)
            {
                alert(radio.id+' checked value is '+radio.value);
            }
        }
    }
    //alert('id='+obj.id + ' value=' + obj.value  +' type='+obj.type);

    return true;
}

```

---

### Post by sarin_cv on 2010-10-27
Thanks.....will try this way...

---

### Post by sarin_cv on 2010-10-27
ya..it works.... but is there any way to do the concatenation which I mentioned above? coz in my code there is a function setField which expects the id... 

for example for radio button it must be setField("radioTest[0]") or setField("radioTest[1]") based on whichever is checked...

so here I need to replace radioTest with obj.id or obj.name... so i gave oit as setField((obj.id)+"[0]") which is not the proper way to append...

---

### Post by gmargo on 2010-10-27
A small matter of programming.....

```

function whichRadio(obj)
{
    var result = "unknown";

    if (obj.type == "radio")
    {
        var idindex = -1;           // index of matching id
        var matchindex = -1;        // index of matching id of checked radio

        // Search elements of form for matching id
        for (var i=0; i < obj.form.length; i++)
        {
            var ele = obj.form.elements[i];
            if (ele.type == "radio" && ele.id == obj.id)
            {
                idindex++;      // matching radio input
                if (ele.checked)
                {
                    matchindex = idindex;   // matching checked radio input
                    break;
                }
            }
        }

        // If a checked radio input of match id was found, then
        // matchindex is not -1.
        if (matchindex >= 0)
        {
            result = obj.id + '[' + matchindex + ']';
        }
    }

    alert(result);
    return true;
}

```

---

### Post by sarin_cv on 2010-10-27
Thanks a lot....this is what I was looking for.... not an expert in javascripts....thats y...

---

