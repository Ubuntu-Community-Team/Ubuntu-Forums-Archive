---
title: "Can't figure out why I get a &quot;xxxxx.parentNode is null&quot; error in javascript"
date: 2009-02-06
forum: Programming Talk
---

### Post by mnemonik on 2009-02-06
Hello everyone, I'm working on a webpage where I have the following javascript code:

[PHP]var bigImg = null;

			

			function makeBig(source) {

				bigImg = document.createElement('img');

				bigImg.style.position="absolute";

				bigImg.style.left=((winWidth() - 800)/2) + "px";

				bigImg.style.top=((winHeight() - 250)/2) + "px";

				bigImg.src=source;

				bigImg.id="bigImg";

				bigImg.onclick=killBig();

			}

			

			function killBig() {

				bigImg.parentNode.removeChild(bigImg);

			}

			

			function showBig(source) {

				if (bigImg !== null) {

					killBig()

				}

				makeBig(source);

			}[/PHP]

Which is supposed to allow me to link thumbnail images with onclick="showBig(source of image)" and display them smack dab center of screen and let me destroy the big image on a second click, but I keep getting an error saying "bigImg.parentNode is null". Is this because it doesn't have a parent, because I just created it? What would I do then? I'm still trying to figure out javascript through and through so all help is very appreciated.

---

### Post by Reiger on 2009-02-06
It's because you have created a loose element which has, sofar, not been attached to a parent in the node tree.
```

var someParent= /* find it */ ;
someParent.**addChild**(bigImg);

```

---

### Post by mnemonik on 2009-02-06
I have been searching like crazy to try and find the answer, and I think you were right about how I created the element but did not place it. I'm pretty sure from all my searching that appendChild is what I need: 

[PHP]var parent = document.getElementById("some_id");
parent.appendChild(bigImg);[/PHP]

So I declared the parent variable outside of my functions, and I put the appendChild line in the makeBig(source) function, so now my code looks like this:

[PHP]
var bigImg = null;

var parent = document.getElementById("content");
 //Declare parent


function makeBig(source) {

	bigImg = document.createElement('img');

	parent.appendChild(bigImg);
 //place the bigImg on the page
	bigImg.style.position="absolute";

	bigImg.style.left=((winWidth() - 800)/2) + "px";

	bigImg.style.top=((winHeight() - 250)/2) + "px";

	bigImg.src=source;

	bigImg.id="bigImg";

	bigImg.onclick=killBig();

}



function killBig() {

	parent.removeChild(bigImg);

	bigImg = null;

}



function showBig(source) {

	if (bigImg !== null) {

		killBig()

	}

	makeBig(source);

}

[/PHP]

And now when I reload the page and try to click a thumb to incur the showBig(source) function, I get this error: "parent is null" referring to the line [PHP]parent.removeChild(bigImg);[/PHP] within the killBig() function. This doesn't make sense because parent is the element with id "content", which I definitely do have in my html...

---

### Post by Reiger on 2009-02-06
It's been a while since I did hardcore JavaScript creating & adding elements from scratch; but here goes a mock up sample using div's & p's for the purpose (and annoying alerts, but hey... ):
```

<html><head>
  <title>Test</title>
  <style type="text/css">
    #content { background: #555599; color:#330000;}
    .child { background: #007733; color: #cccccc;}
  </style>
  <script type="text/javascript">
    var sane=false;
    var kidcount=0;
    
    window.onload=function() {
      container=document.getElementById('content');
      sane = container != null && container != 'undefined';
      if(sane)
	document.body.onclick=eventHandler;
      var msg = 'The test has begun, sanity check: '+(sane ? 'passed, container was found' : 'failed, container could not be found!');
      alert(msg);
    }
    function eventHandler(evt) {
      var element=getSource(evt);
      if(sane) {
	if(element.className=='child')
	  killKid(element);
	else
	  if(element.id=='content')
	    appendNewKidTo(element);
	  
      }
      return sane;
    }
    function getSource(evt) {
      return window.event ? window.event.srcElement : evt.target;
    }
    function initKid( /* in real world case, use params as required ... */) {
      var kid = document.createElement('p');
      kid.className='child';
      kid.innerHTML="I am paragraph no #"+(kidcount+1)+"; click me to remove me...";
      
      return kid;
    }
    function appendNewKidTo(parentElement) {
      var newkid = initKid();
      parentElement.appendChild(newkid);
      kidcount++;
      alert('Added the new kid!');
    }
    function killKid(mykid) {
      mykid.parentNode.removeChild(mykid);
      alert('Killed the kid!');
    }
  </script>
</head><body>
  <div><h2>Sandbox</h2><div id="content">This is my container. Click it to add child paragraphs.</div>
  </div>
</body></html>

```

A couple of remarks about my code:
- I use a top level event handler + event source 'inspection' to keep the 'logic' (interpreting the meaning of the event: did the user add or kill a kid?) contained within a nice central event handler.
- I use the window.onload event/moment to avoid problems with JavaScript's look-ahead evaluation (JavaScript begins executing code ASAP, possibly even before the page is fully loaded) -- simply delaying my JavaScript till I know the browser is ready.
- I use a top level kid counter for user convenience; code wise it might be useful for implementing more complex event handling based on (generated) element IDs.
- I use a sane variable because there's nothing sane to do in a sanity-deprived world.

EDIT: Ooh, and please note that this is a text-based sample -- so only if you click the text will it actually do anything. Shouldn't be a problem with images or buttons, but meh.

---

