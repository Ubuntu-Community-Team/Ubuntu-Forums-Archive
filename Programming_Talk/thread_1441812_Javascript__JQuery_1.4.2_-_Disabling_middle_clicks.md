---
title: "Javascript / JQuery 1.4.2 - Disabling middle clicks on &quot;a&quot; tag"
date: 2010-03-29
forum: Programming Talk
---

### Post by Yuzem on 2010-03-29
Hello,
I want to disable middle click default behaviour to do something else instead. 
In previous JQuery versions I was able to do this:

```
$('a').live('click',function (e) {
        alert(e.button)
        return false
})
```

With that code I was able to do something on middle clicks and also to disable the default behaviour.

Now, with version 1.4.2 I can't do that any more.
Using the 'mouseup' event I can get middle clicks but I can't disable the default behaviour.
I have tried e.preventDefault() or binding both events: .live('click mouseup',etc) but nothing works.

Thanks in advance!

---

### Post by TheBuzzSaw on 2010-03-29
I'm genuinely curious: why? Are you making some kind of game? If your web site is just a normal site, I would be very upset if you attempted to redefine my middle-click behavior. At that point, I'd probably blacklist your site in my JavaScript blocker to regain my freedom. It's not very wise to distort the "normal browsing experience".

I cannot answer your question, though. I only use jquery for effects. I don't know much of the input API.

---

### Post by enz1m3 on 2010-03-29
This may be a shot in the dark, but have you tried using "normal" click() event instead of the live()? Doesn't it work with that also?

Can you give us an url to check what's happening to see if there's a better way to do it?

---

### Post by Yuzem on 2010-03-30
> **TheBuzzSaw said:**
> I'm genuinely curious: why?
I'm coding an application that runs in prism: [Figuritas]("http://yuzem.blogspot.com/p/figuritas.html")
On prism, it doesn't have the middle click problem but I want it to work on firefox also.

> **enz1m3 said:**
> This may be a shot in the dark, but have you tried using "normal" click() event instead of the live()?
I tried from firebug:
```
$('.tabs > .titles a')
.die()
.click(function ()
{
    return false
})
```
... but no luck.
> **enz1m3 said:**
> Can you give us an url to check what's happening to see if there's a better way to do it?
It isn't online but if you install the program you can go to: [http://127.0.0.1:9009/](http://127.0.0.1:9009/)
If you middle click the first tab it opens in a new tab when it should do nothing.

---

### Post by enz1m3 on 2010-03-30
ok, something is really wrong there, and it looks like you're not "pointing" to the right place.

If you do:

```

$('.tabs > .titles a').click(function ()
{
    alert('just a test');
})

```

Does the alert show after or before the new tab opens?

---

### Post by Yuzem on 2010-03-30
It doesn't show at all with middle clicks it only opens a new tab.
With the following the alert shows before the new tab:
```
$('.tabs > .titles a').mouseup(function ()
{
    alert('just a test');
})
```

---

### Post by enz1m3 on 2010-03-30
So I can suppose that code isn't simply executed... try to unbind() before the click() method... it should work that way.

As for the the mouseup, if you change the alert to a return false or use the unbind() before the mouseup(), does it still work as expected (not opening the new tab)?

---

### Post by Yuzem on 2010-03-30
> **enz1m3 said:**
> So I can suppose that code isn't simply executed... try to unbind() before the click() method... it should work that way.
It doesn't work:
```
$('.tabs > .titles a')
.unbind()
.die()
.click(function ()
{
    alert('just a test');
})
```
On middle click it opens a new tab and the alert doesn't show.

> **enz1m3 said:**
> As for the the mouseup, if you change the alert to a return false or use the unbind() before the mouseup(), does it still work as expected (not opening the new tab)?
No, it still opens the new tab:
```
$('.tabs > .titles a')
.unbind()
.die()
.mouseup(function ()
{
    return false;
})
```

---

### Post by enz1m3 on 2010-03-30
Ok, use either unbind or die, don't use both, it's ambiguous.

As for the code, that means the javascript for opening the tab is being done after.

Try adding that jquery code on the end of the html file, right before the end of body tag.

---

### Post by v8YKxgHe on 2010-03-30
Try using [http://api.jquery.com/event.preventDefault/](http://api.jquery.com/event.preventDefault/) instead of return false, may work for you

---

### Post by Yuzem on 2010-03-30
> **enz1m3 said:**
> Try adding that jquery code on the end of the html file, right before the end of body tag.
I tried, the result is exactly the same, same order, first the alert and then the new tab.

> **AlexC_ said:**
> Try using [http://api.jquery.com/event.preventDefault/](http://api.jquery.com/event.preventDefault/) instead of return false, may work for you
I have tried:
.preventDefault()
.stopImmediatePropagation()
.stopPropagation()
Nothing work...
I have tried linking the events to a parent and then detecting the target with e.target.nodeName using .stopPropagation and all the others but nothing works.

---

### Post by TheBuzzSaw on 2010-03-30
> **Yuzem said:**
> I'm coding an application that runs in prism: [Figuritas]("http://yuzem.blogspot.com/p/figuritas.html")
On prism, it doesn't have the middle click problem but I want it to work on firefox also.

Ah, that makes more sense. Cool! :)

---

### Post by enz1m3 on 2010-03-30
Ok...

Can you please try and create a simple html file online only with a link and disabling the middle click like you do (to be sure it's a jQuery 1.4 thing and not some kind of overwrite/incompatibility in your code)?

---

### Post by Yuzem on 2010-03-30
I tried that and the problem persist.
Here is the source:
```
<html>
	<head>
		<script src="web/jquery.js" type="text/javascript"></script>
	</head>
	<body>
		<a href="http://google.com">click here</a>
		<script type="text/javascript">
			$("a")
				.unbind()
				.mouseup(function ()
				{
					e.preventDefault()
					alert("Hello");
					return false;
				})
		</script>
	</body>
</html>
```

---

### Post by enz1m3 on 2010-03-30
Ok, I was finally able to disable middle-click, but I had to call the bind on the document, not the specific element, so you may need to improve the middle-button click check.

Check out [http://www.brunobernardino.com/midclick.html](http://www.brunobernardino.com/midclick.html)

EDIT: Just in case I remove that file accidentally

```

<html>
	<head>
		<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.4/jquery.min.js"></script>
	</head>
	<body>
		<a href="http://google.com">click here</a>
		<script type="text/javascript">
		$(document).ready(function() {
			$("a").bind("click",function(e) {
				alert("e = " + e.button);
			});
			$(document).bind("click",function(e){
				if (e.button == 1) {
					e.preventDefault();
					return false;
				}
			});
		});
		</script>
	</body>

</html>


```

---

### Post by Yuzem on 2010-03-30
Ok, that worked. I will use: e.target.nodeName
Thank you very much!

---

### Post by enz1m3 on 2010-03-30
Please add [SOLVED] to the topic (first post) ;)

---

### Post by Yuzem on 2010-03-31
Done.
Any idea on why it isn't working on the a tag?

---

### Post by enz1m3 on 2010-03-31
Well, I'd say it makes sense if Firefox binds those browser behaviors to the document element and then checks after the event, what's the target, so applying the behavior to an element inside the document wouldn't unbind the default behaviors, but I'm just speculating :)

---

