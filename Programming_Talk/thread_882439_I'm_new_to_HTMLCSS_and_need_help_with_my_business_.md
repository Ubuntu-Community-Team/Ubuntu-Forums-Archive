---
title: "I'm new to HTML/CSS and need help with my business site."
date: 2008-08-07
forum: Programming Talk
---

### Post by 16777216 on 2008-08-07
This is the only place I know of where I might find help for my problem.

My wife and I are trying to start up a business site.
This is the first web site I have ever done, and I am learning HTML/CSS as I go and I seem to be doing good so far but I have a problem.

The problem is we use an other company to handle the phone/payment service and they have a "button" to place in your site.

This "button" is really a table element and ***_nothing_*** can be changed in it.
I need to place it in a consistent place next to the representative's information/photo but I can't seem to get it to do what I want.

Here is the button code ( I have it wrapped in <p></p> tags but the unchangeable part starts at the <!-- click4Advisor button code starts--> and I have removed the src and usemap data just for this post. )

```
				<p id="c4abutton">
				<!-- click4Advisor button code starts-->
				<table>
					<tr><td><div align='center'><img src='REMOVED' border='0' usemap='REMOVED'></div></td></tr>
				</table>
				<!-- click4advisor button code ends-->
				</p>
```

And, this is what the usemap points to.

```
	<!-- Click4Advisor tag starts-->
	<map name='00000'>
		<area shape='rect' coords='0,0,113,67' href='#' onclick='javascript:window.open("REMOVED")'>
		<area shape='rect' coords='2,68,113,86' href='REMOVED' target='_blank'>
	</map>
	<!--Click4Advisor tag ends-->
```

The reason I removed the urls and such is the company has very strict rules as how their code is used and I want to avoid getting our account shut down.

This is the CSS I was trying to use to put it on the right of the representative's information.

```
#c4dbutton {
	float: right;
	margin: 0;
}
```

Am I doing something wrong?

The page this is on is [http://www.giftedguidance.com/index.html](http://www.giftedguidance.com/index.html) ( If putting this link is against the rules I will remove it. I am not trying to SPAM. And, please do not use the site just to "play around." )

Thanks in advance to anyone who can help.

P.S. I am using Ubuntu to make this site and the host server is running Debian. :)

---

### Post by Rocket2DMn on 2008-08-07
Moved to Programming Talk, somebody here should be able to help you with your problem.  Good luck.

---

### Post by k@e on 2008-08-07
I'm not certain about what you want it to do and how it is different from now.

You should reallly validate your html and sort out most of the errors until it's valid: [http://validator.w3.org/](http://validator.w3.org/)

---

### Post by 16777216 on 2008-08-07
I wanted to make the "button" sit on the left or right or perhaps under the photo but, have it align with the photo/introduction in a consistent way, not just next to the picture near the bottom right on one then under the picture on the next then halfway up the photo on the one after that.

Yeah, most of the errors have to do with the button it's self the last time it was checked.

You are right, I need to check again to see if I introduced any new errors myself.

And thanks for moving this to a more appropriate topic. :)

---

### Post by dileepm on 2008-08-07
Try the following

[HTML]
<table>
<!--Block starts-->
<tr>
<td>Photo goes here</td><td rowspan=2>Information/Text goes here</td>
</tr>
<tr>
<td>The advisor code goes here</td>
</tr>
<!--Block ends-->
</table>
[/HTML]
You probably dont need a CSS for alignment you may do it in your HTML itself...
Repeat the block as many entries as you need

:) Let me know a different layout if you need i will provide you the better HTML code...

---

### Post by Tomosaur on 2008-08-07
You could probably do this a few different ways. The 'standard' way (or, more accurately, the correct way) would be to simply work out how to position **everything** correctly using CSS. People often mistakenly use styling and positioning in both the HTML and CSS, which causes a weird hybrid and makes future maintenance a nightmare.

The long and short of it is that you should thing about your page as a series of elements. At its most basic level, this is all HTML is - a list of elements. The CSS does all of the styling and positioning.

If I understand you correctly, you want the following horizontal order for each advisor: 
```
Photograph > Text > Click4Advisor button
```

This is easily accomplished using the <div> element. Here's what I mean:

```

<div class="advisor_row">
        <div class="photograph"><img src="images/photos/advisor1.jpg"/></div>
        <div class="advisor_info">Blah blah blah</div>
        <div class="click4_button">
                <!-- Put the click4advisor button code here-->
        </div>
</div>

```

Then all you need to is create the CSS styling for each of these different div classes, for example:
```

div.advisor_row{
        height: 100px;
        width: 400px;
}

div.photograph{
        position:relative;
        height: 100px;
        width: 100px;
        top: 0px;
        left:0px;
}

div.advisor_info{
        position:relative;
        height: 100px;
        width: 200px;
        top: 0px;
        left: 100px;
}

div.click4_button{
        position:relative;
        height:100px;
        width: 100px;
        top: 0px;
        left: 300px;
}

```

My web dev skills are a little rusty, but I think that should at least get you most of the way there.

Either way - try to avoid using tables, they're a nightmare. Divs are best for creating a regular, layout, and are far more versatile. Only use tables when you're actually trying to display information which should be in a table.

Failing that, you could always try using a CMS (Content Management System) like Joomla - my personal favourite - or Drupal. This will give you a very professional looking website in minutes, and you won't need to worry about the actual coding (of course, being able to code a website is valuable knowledge!).

A CMS really takes the headache out of actually coding your website from scratch, and lets you focus on the content, which at the end of the day is what really matters. Best of all, they come with templates which you are generally free to modify to suit your needs and desired style. The most that is required then is basic CSS knowledge and a bit of HTML to get rid of elements of the style you don't want / need. The downside with this is that a LOT of templates (particularly for Joomla) use lots of tables. There is a fairly big push for template developers to create tableless templates to allow for greater flexibility, but it's not really a big deal.

And of course - the absolutey **best** thing about CMSs are the plugins and modules which you can use to add features to your website. A lot of people think CMSs are only really useful for websites which have a lot of content, but really, they make life so much easier it's hard to think of a reason **not** to use one. Of course, your host will need to support your chosen CMS, but that's not a big barrier really, and you can always switch hosts if you want to.

---

### Post by 16777216 on 2008-08-07
Thanks guys, :KS I will try both methods to see which one works best for my situation.
I will probably do this tonight and update you but, I am in quite a bit of pain right now. ( I broke 2 bones in my shoulder and a rib Monday :( But, I'll get better. :) )

---

### Post by 16777216 on 2008-08-08
Thank you Tomosaur your Idea seems to work out for me the best.
And also thanks to dileepm for your advice as well.
I will try to find more help and tutorials somewhere soon so that I can do this on my own and get good results.

---

