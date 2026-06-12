---
title: "Firefox issue with bank website"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Jnetty99 on 2008-10-08
I been testing Ubuntu on a virtual environment. My goal is to install Ubuntu on a Dell machine that a family member uses. Windows XP, eventually always starts to slow down and act weird. 
All they do in the computer is check emails and check their bank statements. 

Problem i'm having is with Firefox. I want to put a website shortcut on the desktop to access Citibank online. When I go to the site I get the following message.

"You're using a browser or operating system that can't take advantage of all the features at citibank.com."

On the bottom of the screen you click continue and get to the bank account login. If I close the window and try to open the link again, I get the same message again. So each time you always have to click the continue button. This doesn’t happen on Windows. 

Is there a way to trick the website or modify something to make it stop.

---

### Post by chuckyp on 2008-10-08
You need to download the user agent switcher add on for firefox. You can then make the citibank site think you are using IE or whatever browser you want.

---

### Post by superprash2003 on 2008-10-08
well thats because that site works best on windows and IE.. so that would keep popping up whenever you open it of ff

---

### Post by SunnyRabbiera on 2008-10-08
Yeh crap like this is known to happen, especially with using firefox 3 as it identifies itself as firefox 3.
But yes there is a way to trick sites into believing you are using IE7:
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

> **superprash2003 said:**
> well thats because that site works best on windows and IE.. so that would keep popping up whenever you open it of ff

Feh, IE has been surpassed many times by firefox and Opera but its still the ol workhorse because web developers are lazy and ignorant of alternate browsers.

---

### Post by oldsoundguy on 2008-10-08
The only issue I have had with Firefox at my banking site was that I have to enable third party cookies in order to activate the bill pay feature.

And I use a small regional bank.

Since IE now has only 48% of the browser market and decreasing at about a 2% rate per month, time for some sites to pull their head out!!  A NASTY letter to them is called for. (it is not THEIR money .. it is YOUR money!)

---

### Post by SunnyRabbiera on 2008-10-08
> **oldsoundguy said:**
> The only issue I have had with Firefox at my banking site was that I have to enable third party cookies in order to activate the bill pay feature.

And I use a small regional bank.

Since IE now has only 48% of the browser market and decreasing at about a 2% rate per month, time for some sites to pull their head out!!  A NASTY letter to them is called for. (it is not THEIR money .. it is YOUR money!)

Thats a horrid practice by your bank, really you should get them aware of issues with that kind of behavior.

---

### Post by Nxion on 2008-10-08
> **oldsoundguy said:**
> The only issue I have had with Firefox at my banking site was that I have to enable third party cookies in order to activate the bill pay feature.

And I use a small regional bank.

Since IE now has only 48% of the browser market and decreasing at about a 2% rate per month, time for some sites to pull their head out!!  A NASTY letter to them is called for. (it is not THEIR money .. it is YOUR money!)

It is sad that in this day and age that people are so set in there primitive ways. They just don't want to catch up with the times.

---

### Post by Jnetty99 on 2008-10-08
> **chuckyp said:**
> You need to download the user agent switcher add on for firefox. You can then make the citibank site think you are using IE or whatever browser you want.

that's great news. Im going to try it out now. once this is fixed then i'm good to go.

---

### Post by richg on 2008-10-08
I get the same with my small local bank. Even if I click, Do not show this window  
No big deal. I learned some years ago, Change is inevitable, struggle is an option. I just go with the flow.
This is what the bank supports.

Windows

    * Firefox 1.5
    * Firefox 2.0
    * Internet Explorer 6
    * Internet Explorer 7
    * AOL 9.0

Macintosh

    * Firefox 1.5
    * Firefox 2.0
    * Safari 3.0
    * Safari 3.1

Linus still works just fine. No big deal. Linux has barely 1 percent of the desktop market. Macintosh has at least 5 percent of the market and is in the news a lot.
Linux is FAR too much fragmented to be taken seriously.
Maybe Ubuntu will help change that image since Ubuntu news is showing up more & more.

Rich

---

### Post by Jnetty99 on 2008-10-08
I added the add-on and it works. But once you close the browse it resets and goes back to the default setting. 
You can change that under about:config by adding the following string.
useragentswitcher.reset.onclose false.

---

### Post by oldsoundguy on 2008-10-08
> **SunnyRabbiera said:**
> Thats a horrid practice by your bank, really you should get them aware of issues with that kind of behavior.

Not really, since they are using a separate server for bill paying.  I can see the reason why for the extra cookie.  I already have to go through 2 separate sign in procedures in order to access my account.  They were one of the first banks in the US to instigate such stringent protocols, and I am all for it.

They have their site set up to work with ALL browsers and even have it working for Chrome.

Shame some of the "big boys" don't think that universal access is important!

---

