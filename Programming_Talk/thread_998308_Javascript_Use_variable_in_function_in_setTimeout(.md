---
title: "Javascript: Use variable in function in setTimeout()?"
date: 2008-11-30
forum: Programming Talk
---

### Post by secondstage on 2008-11-30
The goal of this code is to
1.) On mouse over, change the image to image1.jpg

2.) On mouse out, change the image to image2.jpg, then after 250 ms, change it to image0.jpg, but for some reason it doesn't work.

Here are the functions...
```
function roll(img_name, img_src) {
	document[img_name].src = img_src;
}


function onOUT(imgSRC0, imgSRC1, imgNAME) {
	roll(imgNAME, imgSRC0);
	setTimeout("roll(\'imgNAME\', \'imgSRC1\');", 250);
}
```

Here is where they are called...
```
<a href="/page2.htm" onmouseover="roll('one', 'image1.jpg')" onmouseout="onOUT('image2.jpg','image0.jpg', 'one')">
<img src="image0.jpg" alt="View the other page" name="one"/>
</a>
```

I think that it has something to do with the setTimeout(...) in the function onOUT(), but I could be wrong.

---

### Post by drubin on 2008-11-30
> **secondstage said:**
> The goal of this code is to
1.) On mouse over, change the image to image1.jpg

2.) On mouse out, change the image to image2.jpg, then after 250 ms, change it to image0.jpg, but for some reason it doesn't work.

Here are the functions...
[PHP]function roll(img_name, img_src) {
	document[img_name].src = img_src;
}


function onOUT(imgSRC0, imgSRC1, imgNAME) {
	roll(imgNAME, imgSRC0);
	setTimeout("roll(\'imgNAME\', \'imgSRC1\');", 250);
}[/PHP]

Here is where they are called...
```
<a href="/page2.htm" onmouseover="roll('one', 'image1.jpg')" onmouseout="onOUT('image2.jpg','image0.jpg', 'one')">
<img src="image0.jpg" alt="View the other page" name="one"/>
</a>
```

I think that it has something to do with the setTimeout(...) in the function onOUT(), but I could be wrong.
[http://www.devx.com/tips/Tip/13646](http://www.devx.com/tips/Tip/13646)

You have your onOut function a little bit off.
[PHP]function onOUT(imgSRC0, imgSRC1, imgNAME) {
	roll(imgNAME, imgSRC0);
	setTimeout("roll("+imgNAME+"," +imgSRC1+");", 250);
}[/PHP]

You are wanting to buld up the function with the input params. (see the concatenated string). You were just "add" the var names to the function and not the values.

Hope this explains it.
EDIT:
The syntax highlighter helps explain the concat better then I could.

---

### Post by csilviu on 2008-11-30
Check this code:
```

<script>
var tt=null;
function roll(img_name, img_src) {
	document[img_name].src = img_src;
	if(tt!=null)
	 clearTimeout(tt);
}


function onOUT(imgSRC0, imgSRC1, imgNAME) {
	roll(imgNAME, imgSRC0);
	tt=**setTimeout("roll(\'"+imgNAME+"'\, \'"+imgSRC1+"\');", 250);**
}
</script>

```
Your code is calling roll() with 'imgNAME' , 'imgSRC1' as arguments, not image name and 'imageX.jpg'.
Plus, you probably must reset timeout, if any, in onmouseover event. To see what's happend if not, increase delay from 250 to 1000ms, and quickly move mouse pointer over and out image couple of times.

---

### Post by secondstage on 2008-11-30
@csilviu: Could you go into detail about the use of tt?

If each image-link had its own function to call, would tt have to be used?

---

### Post by csilviu on 2008-12-01
I think yes, and you need a distinct id for each call of setTimeout() .

---

### Post by tomkravitz on 2008-12-02
I found that using setTimeout() with a js variable was quite confusing. I was going nuts playing with double quotes and single quotes and leading slashes with no luck, until I came up with this method.

1) Write out the function in pure javascript.
2) Wrap the function in an alert() and edit it until it looks like the function you want to execute.
3) Copy and paste it into setTimeout().

I'll keep this example generic - lets say we have a function doSomething() which expects a single variable which in this case will be equal to 'Hello World'

normally we would write: doSomething(variable);

now lets wrap it in an alert() - our goal is to have the alert say "doSomething('Hello World')" not "doSomething(variable)" 

so our alert would look like: 
alert("doSomething(\'" + variable + "\')");

now we have something we can just copy and paste into the setTimeout() 

final result:
setTimeout("doSomething(\'" + variable + "\')", 2000);

---

