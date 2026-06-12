---
title: "website  css position and html question."
date: 2009-03-31
forum: Programming Talk
---

### Post by hockey97 on 2009-03-31
Thread Closed!!!

---

### Post by Tibuda on 2009-03-31
Install an OS in VirtualBox and change the guest machine resolution.

---

### Post by hockey97 on 2009-03-31
I could test it by just resizing my web browser. 

I notice that where the ads are it would move under the main part of the website.

How do I  make is stationary. I don't mind that the user would have to scroll.

I just need to make it not go under or above the main part of the site nor have it move based on others resolution.


My question is how do I make the ad area meaning the blue box to not move. 

I mean I want it so that if a lower  resolution use views the site they will have to scroll horizontally. I don't want the boxes to adjust to the user's web browser.

So I just want to force a scroll meaning the box stay where they are at and if it's off screen they can scroll to it.

Do you think I would need to put a container??  

so the container will hold the blue boxes??

The problem right now is that the blue box adjusts when the screen's width gets smaller and the blue boxes would go under the main website or above it.

---

### Post by Tomosaur on 2009-03-31
Basically (save to html file and view in firefox):

```

<html>
<head></head>
<body>
<div id="left" style="float: left; height: 100%; width: 25%; background-color: blue;"></div>
<div id="middle" style="float: left; height: 100%; width: 50%; background-color: red;"></div>
<div id="right" style="float: left; height: 100%; width: 25%; background-color: green"></div>
</body>

```

IE will probably mess this up. An easy way to work around IEs box model problems is to always use just a bit less than 100% of the total width of the page (reduce every % in the above by 1, for example).

---

### Post by hockey97 on 2009-03-31
> **Tomosaur said:**
> Basically (save to html file and view in firefox):

```

<html>
<head></head>
<body>
<div id="left" style="float: left; height: 100%; width: 25%; background-color: blue;"></div>
<div id="middle" style="float: left; height: 100%; width: 50%; background-color: red;"></div>
<div id="right" style="float: left; height: 100%; width: 25%; background-color: green"></div>
</body>

```

IE will probably mess this up. An easy way to work around IEs box model problems is to always use just a bit less than 100% of the total width of the page (reduce every % in the above by 1, for example).

What would that do? 


Like if I make a div that uses css properties like using above the float and the rest. 

Would I make the div to have all the website inside the div that has those properties you suggested?

---

### Post by Tomosaur on 2009-03-31
> **hockey97 said:**
> What would that do? 


Like if I make a div that uses css properties like using above the float and the rest. 

Would I make the div to have all the website inside the div that has those properties you suggested?

The div with id 'left' appears on the left. Put everything you want in the left of the page in there.

The div with id 'middle' appears in the middle. Main page content goes in here.

The div with id 'right' appears on the right.

Basically put the adverts in the left and right divs, then put the main content in the middle. Obviously this is a very simplistic layout but it will give you the three column look you're going for.

EDIT: Woops - I misunderstood the question.

If you don't want something to resize with the window, then you need to be explicit in its size. You should use pixel values rather than percentages or ems.

---

### Post by hockey97 on 2009-03-31
> **Tomosaur said:**
> The div with id 'left' appears on the left. Put everything you want in the left of the page in there.

The div with id 'middle' appears in the middle. Main page content goes in here.

The div with id 'right' appears on the right.

Basically put the adverts in the left and right divs, then put the main content in the middle. Obviously this is a very simplistic layout but it will give you the three column look you're going for.

EDIT: Woops - I misunderstood the question.

If you don't want something to resize with the window, then you need to be explicit in its size. You should use pixel values rather than percentages or ems.

well, I already use px. 

The position was absolute but then I changed it to fixed.  I have a vertical scroll. So when the user scrolls the ads won't move.

yet when the width is smaller  the  ads move inwards and at a 800x600 resolution  the  ads appear behind the main part of the website.

I just want the ads to stay put. If the screen gets smaller then I want the users to just be able to scroll horizontal. 

if you look at the link I gave on the first post. 

resize your browser you will see what I mean. The blue boxes will resize and also move inwards.

---

### Post by hockey97 on 2009-04-01
HI, So you say that I should just use px instead of %?

I am using px.  Does it matter on the position setting?

I had it at absolute and then I changed it to fixed.

the ceo of the company is picky. He is also breathing down my neck.

He wants me to upload this website as soon as possible and I just missed the deadline because of the ads adjusting.

Does anyone have suggestions on what I could try to do?

the only problem is that the ads (blue boxes) resizes and also moves inward when the browser screen gets smaller.

I mean it's pixel perfect on my monitor. It's just when I tried it on my sisters laptop and also my dads computer which is old.

The site ads and also one text would get shifted. 


I want them to be stationary not moving at all. Even if they end up off screen I want a scroll to appear and not see them adjusting to the screen size.

I currently have them in a fixed position using px.  The ads will not move even when I scroll up and down but it will move if the window width gets smaller.

---

### Post by hessiess on 2009-04-01
Link is eather dead or very slow.

---

### Post by hockey97 on 2009-04-01
no, sorry... my ISP just gave me a new ip address and I need to update the right ip to transfer traffic to my server.

the link should work now.

---

### Post by hockey97 on 2009-04-01
when you look at the site. You will see on the right and left blue boxes.

These blue boxes will contain ads.

Now the problem is that the smaller the resolution and the smaller the screen gets the more the ad on the right moves inward towards the left.

This at some point will make the ad on the right move right into the main part of the website and be behind the main part of the website.

I want it so that  if the resolution is small it will have to scroll horizontally. 

I don't want the ad on the right to resize or adjust to smaller resolutions.

I want to force a scroll if the resolution is smaller.

Is their a way to do this? I have the position fixed.

Any idea? If you take a look at the site and then resize your browser you will understand what I am saying.

I don't want any element to adjust with the screen but if the stuff goes off screen I just wan scrolls to appear so people can just scroll around the site.

I don't want to see elements moving when the screen gets resited to smaller resolutions.

What should I do?

---

