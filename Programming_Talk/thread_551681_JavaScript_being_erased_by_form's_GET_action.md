---
title: "JavaScript being erased by form's GET action"
date: 2007-09-15
forum: Programming Talk
---

### Post by mrpeenut24 on 2007-09-15
I'm writing a simple conversion tool using html/js and don't currently have *too much* experience in javascript.  I'm using a form with textboxes and a submit button to initiate the conversion, however, when I push the submit button, the form's GET essentially sends me to a new page and erased the info set by the javascript.  Here's what I'm talking about:

```

<form>
  <textarea style="background-color: lightyellow;" name="conversion"></textarea>
  <br>
  Convert from 
  <select name="convertFrom">
      <option value="text">Text</option>
      <option value="hex">Hex</option>
      <option value="binary">Binary</option>
  </select>
  to
  <select name="convertTo">
      <option value="text">Text</option>
      <option value="hex">Hex</option>
      <option value="binary">Binary</option>
  </select>
  <br>
  <textarea style="background-color: pink;" name="converted"></textarea>
<br>
<button  onclick="action1(conversion, convertFrom, convertTo, converted);">Convert</button>
  <br>
  
</form>

```This writes the converted data to the second textarea using ```
converted.value=convertedData;
```This writes it to the text area, but as soon as it does, the page is redirected with the GET method and all the data is erased.  Is there some postback-ish way I should be doing this?

Thanks.

---

### Post by mrpeenut24 on 2007-09-17
I hate bumping my own thread, but google isn't turning anything useful up.

---

### Post by LaRoza on 2007-09-17
> **mrpeenut24 said:**
> 
<button  onclick="action1(conversion, convertFrom, convertTo, converted);">Convert</button>
  <br>
  


Assuming everything else works, add "return false;" to the ECMAScript.

---

### Post by Wybiral on 2007-09-17
You can change the forms "action" to a javascript function and have it process the data without reloading (you'll probably want to learn some DOM control).

---

### Post by LaRoza on 2007-09-17
> **Wybiral said:**
> You can change the forms "action" to a javascript function and have it process the data without reloading (you'll probably want to learn some DOM control).

In a linked file (<script type="text/ecmascript" src="script/script.js"></script>):

[php]
window.onload = function()
{
    document.getElementsByTagName("form")[0].onclick = function()
    {
        //code here
        return false;
    }
}
[/php]

---

### Post by mrpeenut24 on 2007-09-17
> **LaRoza said:**
> Assuming everything else works, add "return false;" to the ECMAScript.

I've got some experience with DOM through using python cgi scripts and a little javascript.

Adding it to the actual function didn't work, but adding it to the button's action did.

I had the form's action set to the function, but I didn't have the return false, so it didn't work. 

Anyway, it's working now.  Thanks for the help guys.

---

