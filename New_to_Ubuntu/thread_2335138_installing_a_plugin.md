---
title: "installing a plugin"
date: 2016-08-25
forum: New to Ubuntu
---

### Post by elmclose on 2016-08-25
Hi everyone,

I have installed Ubuntu for the first time and I am trying to understand the basics of Linux OS. I want to install a plugin for geany editor so that I get the inline encryption working. The plugin is:
[https://github.com/geany/geany-plugins/tree/master/geanypg](https://github.com/geany/geany-plugins/tree/master/geanypg)

I have no idea how to install a plugin. I would be grateful for a step-by-step guide to get me started.

Many thanks in advance,

Davood

---

### Post by Frogs Hair on 2016-08-25
This plug-in may be included with the geany plug-ins package available in the Ubuntu repository. Start by installing the following. ```
sudo apt-get install geany-plugins 
```

---

### Post by elmclose on 2016-08-26
It worked! Thank you very much Frogs Hair. What a joy to be using Ubuntu after years of time wasting with Windows.
What is the command for installing a specific plugin for an app? if fact where can I find a list of important Ubuntu commands?
I know I need to learn a lot. For example:
I copied your command but could not past it into the command window (using CTRL+V) -- so I typed it. I am sure there is a keyboard combination that would do it.

Thank you again for your kind help

---

### Post by leunam12 on 2016-08-26
I think it's Shift+CTRL+V for pasting

---

### Post by uwes on 2016-08-26
In the command line, some shortcuts like ctrl+c are already used, that is why you have to copy with ctrl+shift+c and paste with ctrl+shift+v.

I guess there is no single list of important commands, as it always depends on what you want to do and how you want to do it. Best might be to explain what you just did when installing this plugin:

Ubuntu is a repository-based linux which means that many programms (apps) can be found online in the repositories. The standard repositories are readily available but you can add other repositories, too. However, you should be careful with that as you do put your system at an additional risk of installing malware. Apt-get is the command line programm to install (remove, purge, etc.) packages from the repositories. "Install" is the option what to do with the package and then comes the package name. This a very quick and convenient way of installing new packages with the disadvantage of first having to know the name of what you want to install. The program aptitude is a little more graphical and allows some search options etc. (sudo apt-get install aptitude). And there are other package managers with a modern graphical user interface (gui) like ubuntu-software (should be included) or synaptic (has to be installed, I guess you know how by now) which allow you to surf through lists of available packages with different kinds of sorting. 

As apt-get needs administrator privileges to install packages on your system, you prefix it with "sudo" which grants these admin privileges to the program following it. (This is also why its generally best to be especially careful if you type a "sudo"-command without knowing what its doing.

By the way: in the terminal, the tab-key can be very helpful as auto-complete. If there are several options of how to complete the command / directory / etc. you typed then press it twice to show all available options. This can be very helpful if you don't remember the exact command. It also works for the package names in apt-get.

---

### Post by oldos2er on 2016-08-26
> **elmclose said:**
> II copied your command but could not past it into the command window (using CTRL+V) -- so I typed it. I am sure there is a keyboard combination that would do it.

Try swiping the text you wish to copy, move the mouse cursor to where you want the text pasted, and push the middle mouse button once. Or you can use Ctrl-Ins to copy, Shift-Ins to paste if you prefer the keyboard.

---

### Post by oldrocker99 on 2016-08-26
> **elmclose said:**
> It worked! Thank you very much Frogs Hair. What a joy to be using Ubuntu after years of time wasting with Windows.
What is the command for installing a specific plugin for an app? if fact where can I find a list of important Ubuntu commands?


Here's a quick list: [http://ss64.com/bash/](http://ss64.com/bash/)

Here's a manual which assumes beginner status:[http://vic.gedris.org/Manual-ShellIntro/1.2/ShellIntro.pdf](http://vic.gedris.org/Manual-ShellIntro/1.2/ShellIntro.pdf)

And here's a two-pager "cheat sheet." [http://www.digilife.be/quickreferences/QRC/The%20One%20Page%20Linux%20Manual.pdf](http://www.digilife.be/quickreferences/QRC/The%20One%20Page%20Linux%20Manual.pdf)

---

### Post by Impavidus on 2016-08-26
Good advice given above. The only question not yet answered is:> **elmclose said:**
> 
What is the command for installing a specific plugin for an app?

It depends. If you're lucky, the plugin is packaged (possibly along with some other plugins for the same application) into a package in the Ubuntu repositories. In that case you can install the plugin in the same way as you install the application: using the package manager.

If that's not the case, then there're no rules.Things may be different for each application you want to extend with plugins.

---

### Post by Frogs Hair on 2016-08-26
> Thank you very much Frogs Hair

You're Welcome :)

---

### Post by elmclose on 2016-08-26
Thank you very much oldo2ser, that was a good tip.

---

### Post by elmclose on 2016-08-26
Thanks uwes that was a thorough and thoughtful reply. I learned a lot from it.
It is so refreshing to see how helpful the Ubuntu community is. I am very happy about switching to Linux after years of deliberation.

---

### Post by elmclose on 2016-08-27
> **oldrocker99 said:**
> Here's a quick list: [http://ss64.com/bash/](http://ss64.com/bash/)

Excellent website. Should be in the forum archive for all see.  I spent the best part of the day on the password generator alone!

I would be grateful if you could show me how I could add the bash module for the password generator in my startup profile.

Thanks again oldrocker99 for these excellent links

---

### Post by yetimon_64 on 2016-08-27
> **elmclose said:**
> Excellent website. Should be in the forum archive for all see.  I spent the best part of the day on the password generator alone!
Do you mean [[COLOR=#0000ff]--this--[/COLOR]]("http://ss64.com/pass/pass.html") (blue text is a link to the generator) password generator ?

> **elmclose said:**
> I would be grateful if you could show me how I could add the bash module for the password generator in my startup profile....If the link above is the generator you mention, note the next quote from the page linked ...
> This password generator works using Javascript, entirely within the page It is NOT a bash module you can use in your startup profile. You can save the page as a html file and use the generator if the site goes offline though, also a quote from the generator page ...
> ... it is a very good idea to save your own copy of this page. Keeping your  own copy ensures that the password generator will still be available to  you even if this website goes off-line. You can also *View-Source*  and see exactly how the javascript works, copy it to a USB stick, email  it to yourself, even upload it to your own website (it’s open source.)  There are no dependent files, just save as a single HTML file. 

The site gives you express permission to use the javascript code in the source offline, which is very nice of the authors to do so. To do so while on the site go to the "File" menu in your browser and select the "Save page as" menu option. In the save as dialog name the file as you want it on your system, choose the location to save to and finally choose the "Web page, complete" setting (looks better complete than as a single html file, but a plain html file save will work as well) just above the Save button, then press "Save", and you are done. You now have a local copy of the generator page. You can run it by just double clicking on the html file and it should then open locally from the saved files.
  
Regards, yeti.

---

### Post by elmclose on 2016-08-29
Thanks yeti for your reply. The module I was talking about was in this page:
[http://ss64.com/pass/command-line.html](http://ss64.com/pass/command-line.html)

I just copied the script into my bashrc file as suggested by one of the moderators and it worked fine.
Thanks all the same. I am delighted with the help I am getting from you guys. I am really enjoying the power and flexibility of Ubuntu. Everything is so logical and everything works as they should.

---

