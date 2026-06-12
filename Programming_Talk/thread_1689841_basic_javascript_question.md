---
title: "basic javascript question"
date: 2011-02-17
forum: Programming Talk
---

### Post by badperson on 2011-02-17
Hi,
I have this little test function: 

```

function testSetValue(id){

document.getElementById(id).value = 'what???';

}

```

here's the html:
> 

<form id="entryInputForm">
<textarea name="text" id="entryInputArea" rows="20" cols="105" > </textarea><br/>
	<input type="submit" value="hello!" onClick="testSetValue('entryInputArea')"/>

</form>



that code sets the value, but then the text immediately disappears. (I'm setting the value of a textarea)

anyone know what causes that? 
bp

---

### Post by StephenDavison on 2011-02-17
Try changing your button from type="submit" to type="button".  I think the submit button is triggering a form submission that is reloading your page as the default action.  The content of the text is being reset when the page reloads.

---

### Post by badperson on 2011-02-17
gotcha...that worked. thanks!

---

