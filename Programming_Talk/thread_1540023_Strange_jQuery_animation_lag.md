---
title: "Strange jQuery animation lag"
date: 2010-07-27
forum: Programming Talk
---

### Post by .:PiXi²:. on 2010-07-27
Hi

With the website I'm currently working on, I have this strange problem while animating some elements with jQuery.
Instead of trying to explain what's going wrong, I've made a sample of the problem. Have a look at this: **[http://www.zupa.be/AnimationLag/]("http://www.zupa.be/AnimationLag/")**.
Hover one of the numbers at the upper right corner and click a link. The current green div should close smoothly and the matching div for the clicked link should open smoothly.
This is the function that contains the animations.
[PHP]function setPanelWidth(){
	$('.collapsed').animate({width:28},'fast','linear',function(){
		$('.collapsed *').css('visibility','hidden');
		var w = $('#main').width()-2;
		$('#main').children('.collapsed').each(function(){
			w -= $(this).width()+2;
		});
		$('.panel *').css('visibility','visible');
		$('.panel').animate({width:w},'fast','linear');
	});
}[/PHP]
All of you who know something about jQuery, just take a look at **[http://www.zupa.be/AnimationLag/]("http://www.zupa.be/AnimationLag/")**, open the source, take a look at the script and make my day.

Thanks in advance!

---

### Post by enz1m3 on 2010-07-28
Well, at a glance, I don't see anything that could be causing too much trouble...

If you use ```
$('.collapsed *').hide();
``` and ```
$('.panel *').hide();
``` does it work faster?


Also, try to put

```

$('.collapsed *').css('visibility','hidden');
var w = $('#main').width()-2;
$('#main').children('.collapsed').each(function(){
	w -= $(this).width()+2;
});

```

Before the 

```
$('.collapsed').animate()
```

to try and make it get to the resize animation faster.

---

### Post by WitchCraft on 2010-07-28
stackoverflow.com is a good forum for JQuery questions.

This forum is more Linux-centric. 

While it's allowed to post a Linux-unrelated question here, that doesn't mean it's a good idea.
You'll probably get a better answer much faster, there.

---

### Post by .:PiXi²:. on 2010-07-29
Thanks for the responses, I got it solved now.

---

