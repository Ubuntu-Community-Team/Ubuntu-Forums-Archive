---
title: "Browser error Epiphany not working"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by aka-John99 on 2013-02-24
I am still trying to fnd my feet with Ubuntu. 

Epiphany is a lightweight (is it or was it the default ) browser but it is not working. I do not see options for troubleshooting and fixing it.

I have Google Chrome and various versions of Firefox installed and working. Epiphany has worked previously on this machine. For some reason it does now not work everything gives an error of:
**[SIZE=1]Oops! It was not possible to show this websit[SIZE=1][SIZE=1]e[/SIZE][/SIZE][/SIZE]**

[SIZE=1]Errors like [/SIZE]

[COLOR=#000000][FONT=Ubuntu]The website at **[http://www.google.com/search?client=ubuntu&channel=es&q=%s&ie=UTF-8&oe=UTF-8](http://www.google.com/search?client=ubuntu&channel=es&q=%s&ie=UTF-8&oe=UTF-8)** seems to be unavailable. The precise error was:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]*Cannot resolve proxy hostname ()*[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
Anyone have ideas ?

[B][SIZE=1][SIZE=1] 
[/SIZE][/SIZE][/B]

Using Ubuntu 12.04 on a 64 bit AMD laptop

---

### Post by aka-John99 on 2013-02-26
Bump !

Is anyone able to offer advice, or say what further information  you may require in order to provide suggestions please.

Thanks in advance.

---

### Post by DuckHook on 2013-02-26
I don't use Epiphany, but if your other browsers are working and Epiphany is not, then you have narrowed the problem down to Epiphany itself. Furthermore, if you get a proxy error, then it is logical to look at whether Epiphany settings somehow flipped to expecting a proxy. If you are not connecting through a proxy, navigate into Epiphany's settings and turn proxy off. If you are using a proxy, then navigate to the same settings and type in the proper proxy values.

---

### Post by aka-John99 on 2013-03-02
Thanks for the reply. 

I do not see any option relating to proxy settings. Epiphany is only there as an aditional browser, mainly just in case the others do not work and I am not familiar with the use and setup options. It seems to only have two menus.
[LIST=1]
[*]a **cog icon**. This is mainly edit and new tab options 
[*]a **Web** menu on the top task bar or what ever it is called
[LIST]
[*]this includes a **Help **option, and opens an offline Gnome Epiphany Manual. I have attempted to look through that but do not see any mention of proxy settings. 
[*]and **preferences**, that has four tabs: General,Fonts & Style, Privacy & Language. Again no mention of proxy. 
[/LIST]
   
[/LIST]

I do wonder if the menu sytem may be broken. For instance the manual says > *"*[COLOR=#3C3C3C][FONT=sans-serif]*Epiphany*[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif] stores your cookies and passwords in the Personal Data Manager which can be accessed by choosing [/FONT][/COLOR][COLOR=#6C6C6C][FONT=sans-serif][COLOR=#6C6C6C]Edit[/COLOR] &#9656; [COLOR=#6C6C6C]Personal Data[/COLOR][/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif].[/FONT][/COLOR]*" * I do not see any edit meu.

Maybe I should just give up on Epiphany & try something else like
[LIST]
[*]Links 2  [http://links.twibright.com/](http://links.twibright.com/)
[*]or Midori [http://twotoasts.de/index.php/midori/](http://twotoasts.de/index.php/midori/)
[/LIST]

---

### Post by vasa1 on 2013-03-02
Based on what I've read, Epiphany (or Web) "works best" with GNOME. You haven't mentioned your desktop environment. My understanding is that Epiphany relies a lot on features available in a complete GNOME environment. While Unity does have some GNOME components, it's possible that something more is needed.

I've played a while with Epiphany and Midori in the past but couldn't quite adjust to their minimalism.

---

### Post by aka-John99 on 2013-03-02
Ok then I guess that may be the problem, even though it has run in the past. DE is Unity and usually the 2D verson. 

Any method of checking depedancies,or would simply reinstalling possibly help.

---

### Post by aka-John99 on 2013-03-02
Epiphany / Web
I have now discovered this confirmed but unasigned bug[I][SIZE=2] 
[/SIZE][/I]
[LIST]
[*]*[SIZE=2]"Web" menu missing from Epiphany on Unity[/SIZE]"* [https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/954603](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/954603)
[*]Duplicate of a fixed bug "*Add GMenuModel support to AppMenus*"[ ]("https://bugs.launchpad.net/indicator-appmenu/+bug/950084")[    https://bugs.launchpad.net/indicator-appmenu/+bug/950084]("https://bugs.launchpad.net/indicator-appmenu/+bug/950084")
[LIST]
[*]What does *Milestone Application Menu Indicator 0.3.95 indicate *?
[*]Should this now work on Ubuntu 12.04 LTS Unity?
[/LIST]
[/LIST]
[TABLE="class: listing"]
[TR="class: highlight"]
[TD]                         

Midori
I had hoped that would work, and found something suggesting it is or was supported by Unity [SIZE=2]"[/SIZE]*[SIZE=2]Web-browser Midori Adds Unity Support and Neat ‘Next Page’ Feature," [/SIZE]*[http://www.omgubuntu.co.uk/2011/08/midori-0-4-0-adds-speed-style](http://www.omgubuntu.co.uk/2011/08/midori-0-4-0-adds-speed-style) but that gives a similar error message to Epiphany

[/TD]
[/TR]
[/TABLE]

---

