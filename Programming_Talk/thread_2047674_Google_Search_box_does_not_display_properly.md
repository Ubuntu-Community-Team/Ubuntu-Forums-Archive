---
title: "Google Search box does not display properly"
date: 2012-08-25
forum: Programming Talk
---

### Post by Whitesman on 2012-08-25
Hi,
I was wondering if anyone can help me with an issue I have with Firefox on Ubuntu.   I mess around trying to develop websites which ...yes i know are quite amateurish. I have incorporated a Google search box which works fine with Windows on both IE and firefox but some how doesn't work on Ubuntu.

On [http://www.middletonia.co.uk](http://www.middletonia.co.uk) the box is all squashed up( see top left of page).  I have applied style to the search box in external style sheet style.css.   The button to start the search is under the writing as I have defined the width as width:213px; and this is important to the right width on Windows.

On [http://www.thenatureofthegods.co.uk](http://www.thenatureofthegods.co.uk) the Google search box has no width and ends up being far too large.   I am assuming that this is the fault of Ubuntu.  I was hoping that there might be an easy solution to this but when I change one thing its affects windows differently then Ubuntu.  while Firefox and IE on windows work consistently.

Any suggestions?

Paul Whitesman

---

### Post by nothingspecial on 2012-08-25
*Thread moved to **Programming Talk**.*

---

### Post by ofnuts on 2012-08-26
> **Whitesman said:**
> Hi,
I was wondering if anyone can help me with an issue I have with Firefox on Ubuntu.   I mess around trying to develop websites which ...yes i know are quite amateurish. I have incorporated a Google search box which works fine with Windows on both IE and firefox but some how doesn't work on Ubuntu.

On [http://www.middletonia.co.uk](http://www.middletonia.co.uk) the box is all squashed up( see top left of page).  I have applied style to the search box in external style sheet style.css.   The button to start the search is under the writing as I have defined the width as width:213px; and this is important to the right width on Windows.

On [http://www.thenatureofthegods.co.uk](http://www.thenatureofthegods.co.uk) the Google search box has no width and ends up being far too large.   I am assuming that this is the fault of Ubuntu.  I was hoping that there might be an easy solution to this but when I change one thing its affects windows differently then Ubuntu.  while Firefox and IE on windows work consistently.

Any suggestions?

Paul Whitesman
Both look OK to me, on "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:14.0) Gecko/20100101 Firefox/14.0.1" (see attachment)

---

### Post by vasa1 on 2012-08-26
The Middleton one shows up properly in Opera 12 as well ...

---

### Post by Whitesman on 2012-08-26
> **ofnuts said:**
> Both look OK to me, on "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:14.0) Gecko/20100101 Firefox/14.0.1" (see attachment)
 
That does surprise me as I have the latest ubuntu download on my pc  with update-to-date Mozilla and the Search button (on Middletonia site) is buried under the text.   I'm not on my linux pc now but I will have to send you a pic.  I can see from your photos that both seem okay which is great news.  
 
It's the 'Middletonia' site [http://www.middletonia.co.uk/home.html](http://www.middletonia.co.uk/home.html) that is worst affected and I have put the search box on every page.  I have had to decide to leave it as it is because I can't correct it. On 'The Nature of the Gods' [http://www.thenatureofthegods.co.uk/](http://www.thenatureofthegods.co.uk/) it is just the input box itself is very much wider than it appears on Windows in either Mozilla and IE. I wonder then why I can see this on my system and you can't?  Any ideas?

 
Thanks for taking the time to look and hopefully if I can send you some photos when I get back to my flat tomorrow you can have a peep and see what you think.
 
Paul

---

### Post by Whitesman on 2012-08-27
Hopefully you will be able to see attachments.   Middletonia (the first image) has the non functioning squashed Google box and The Nature of the Gods has an extra wide search box.   The later is not important as I made room for is when I realised what was happening.  The former is a problem because this has been copied onto the hundred and odd pages of the site.  

I am using the latest Ubuntu, which I forget the name of now but have it set to the classic view as I don't like the Unity bar. 

Any ideas?

Paul

---

### Post by snip3r8 on 2012-08-27
Even works on iPad

---

### Post by Whitesman on 2012-08-27
> **snip3r8 said:**
> Even works on iPad


Hi thanks for that. I'm glad to hear the sites work well on iPad as a lot of people seem to use them these days.  If you look at my post above I have included two snapshots which will show you the problem I am having on Firefox on Ubuntu OS. Firefox on Windows works okay as do most other browsers.  I have other problems with browser on Android phone OS  but I was concerned that I could not get the Google search box working on Ubuntu and I have no idea why. I can't help thinking there must be a solution to this.

---

### Post by greenpeace on 2012-08-29
hi, 
I can see the overlap you mention on Firefox on ubuntu, but it looks fine on Chrome.

Consider setting the width of the search box as part of the style, and remove the **size=18** property from the <input> tag

When I replace it here with **width:10em;** (just add to the style="" property on the tag if you want to test it) it looks good on Chrome and Firefox.

I'm not sure how that appears on Windows, but hope it helps.

---

### Post by greenpeace on 2012-08-30
Also, for the [http://www.thenatureofthegods.co.uk/](http://www.thenatureofthegods.co.uk/) site, you can use the same trick... 

... just set the desired width of the field in the style of the <input> tag!

I just had a look on Windows and it looks fine if you make that change.

Let me know how it goes (and don't forget to mark it solved if it all comes out ok!)

---

