---
title: "web programming help."
date: 2008-02-08
forum: Programming Talk
---

### Post by hockey97 on 2008-02-08
Hi I am using gimp to create the art for my website.

I am right now working on the buttons. Should I use javascript to make animated buttons??

I want to make a button where when the mouse is over the button not clicked the button would show ice forming slowly when clicked it will be solid frozen with fog comming off the ice.  I want the animation to show water freezing slowly when the mouse is over it but if the person has the mouse over it and then takes it off within like 1min I was the ice to slowly melt. I thought that javascript may be better to control the animations based on events.

any suggestions???

---

### Post by themusicwave on 2008-02-08
To be honest I do more desktop than web programming.

However, you will have to use a client side language like JavaScript.

I am pretty sure JavaScript has an event  called OnMousOver.  You'll want to use that.

A quick google search turned this up, it may help.

[http://www.javascripter.net/faq/onmouseo.htm](http://www.javascripter.net/faq/onmouseo.htm)

have fun,

Jon

---

### Post by LaRoza on 2008-02-08
That can be done with ECMAScript, but would require knowledge of it (not something you could whip on without knowing how).

You might be better of making an animated gif of the actions and using CSS.

(Look up image buttons)

---

### Post by hockey97 on 2008-02-08
thanks for the link it helps. I am googling around trying to find about how I will make the button to control the animation and what pics I would need. So I guess I will have fun with this lol.

---

### Post by eggdeng on 2008-02-09
You will need to use event handlers to call functions which initiate each of the transitions you describe, so the html for the button would look like this. 

```
<input type = "button" id ="mybutton" name ="mybutton" value ="CLICK" onMouseOver="firstfunction(this)" 
onMouseOut="secondfunction(this)" onMouseOut="thirdfunction(this)">
```

(The buttons for the site in my sig work in this way.) To actually implement the transitions using JavaScript is possible but might not be practical in terms of overhead or the smoothness you will be able to achieve. And the necessary functions will be quite difficult to write without a good grasp of JavaScript.

Still, it's a nice idea & would be fun to do so if you are determined to go ahead and you need help writing the functions, post here & I can lend you a hand.

---

### Post by RetiredInMaine on 2008-02-10
If you have the programming skills you can use either javascript or java. However many people turn off both java and javascript for security reasons. Also not all web browsers will interpret your code exactly the same way. The sugustion from a prior post to use an animated gif is probably your best bet if want everyone to see your web site. If you do go the javascript route you need to put in an alt path for those browsers that won't see your button. Actually you should have an alt path for all of your graphics as there are still some people who use a text only browser such as lynx.  Be sure to test your web pages with several different browsers. If you use javascript test with javascript turned off as well as on.

---

### Post by moephan on 2008-02-10
Typically advanced visual effects like this are done in flash these days. This effect would be possible in javascript. For instance, you could use javascript to swap between a series of animated gifs.

HTH

---

