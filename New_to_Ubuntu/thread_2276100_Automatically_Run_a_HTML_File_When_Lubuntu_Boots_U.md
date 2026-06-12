---
title: "Automatically Run a HTML File When Lubuntu Boots Ups"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by serafini-c on 2015-04-30
I have taken an old XP box and I have put Lubuntu onto the system. This company has paid for a service that provides a vet TV online for waiting rooms. which is just like a power point presentation online. I think the website is running Java Script and the website definitely requires Adobe Flash to run. 

My aim is to get Lubuntu to automatically run this HTML File when booting up. The HTML file will automatically open the website and logs the user into the website without any user input. 

I have tried some methods but all require Applications (Desktop Configuration File) to run it does not seem to work with HTML files. 

I have tried going to: 
Preferences > Default Applications For LXSession > Autostart > Manual AutoStarted Applications > +Add > Add HTML File
This did not seem to work. 

I have also tired: 
~/.config/autostart/Input HTML File In Here
This also seem to not work.

The HTML Code I am Wanting to Run Is:

<HTML>
<HEAD>
<TITLE>**INPUT TITLE**</TITLE>
<script>
function loginform() {
document.myform.action = "**[WWW.WEBSITE-INPUT.CO.UK]("http://WWW.WEBSITE-INPUT.CO.UK")**"
document.myform.submit();

}

</script>
</HEAD>
<body onload="loginform ()">
<FORM NAME="myform" Method="POST">
<INPUT TYPE="hidden" Name="username" Value="**INPUT-USERNAME**">
<INPUT TYPE="hidden" Name="userpass" Value="**INPUT-PASSWORD**">
</FORM>
</BODY>
</HTML>

...................................................................................................
Additional Note 

I also can not seem to get this code to open the website in full screen (Firefox, Chrome) any additional help on this would be appreciated. I be creating another forum thread for this issue but thought I might as well ask on here as well.

Thanks for reading this Post.

Kind Regards,
Paul

---

### Post by mcduck on 2015-04-30
Your problem is that HTML files are not programs, so you can't actually run it on it's own.

Instead you'll need to open the file in a web browser, which can then interpret the file and do things based on it.

So in your autostart, instead of trying to run the HTML file you need to run something like this:

```
firefox /full/path/to/yourfile.html
```
(of course replace the path with the actual path to your file)

I'm not sure if Firefox has any command-line option to open in full screen. If not, there are some Firefox extensions for running in Kiosk mode that can do this for you. Like this one: [https://addons.mozilla.org/en-US/firefox/addon/r-kiosk/]("https://addons.mozilla.org/en-US/firefox/addon/r-kiosk/")

---

### Post by TheFu on 2015-04-30
If is possible to pass the URL as an argument to firefox.

firefox [http://google.com](http://google.com)
You can specify userid/password inside the URL in the normal way.

Also, I think there is an option to start is kiosk-mode. Check the manpage - though I recall the firefox manpage sucks.

---

### Post by serafini-c on 2015-04-30
I have just used a Firefox add-on. Which is not ideal but it suits my needs. The add-on is called R-Kiosk (Mentioned by [**[COLOR=black][FONT=&quot]mcduck[/FONT][/COLOR]**]("http://ubuntuforums.org/member.php?u=17309")).

R-kiosk
[URL="https://addons.mozilla.org/en-US/firefox/addon/r-kiosk/?src=search"]https://addons.mozilla.org/en-US/firefox/addon/r-kiosk/?src=search

[/URL]

  This extension defaults the browser to full screen, disables all menus, toolbars, key commands and right button menus. Alt+Home still takes you home.


  This add-on is a bit overkill for what I need as I only really need one website opening in full screen and I do not need anything disabled. Ideally I would like to use some form of code to create this solution but this add-on suits my need enough to implement on site. 


  Thanks for all your support 
  Kind Regards,
Paul

---

### Post by serafini-c on 2015-04-30
I have managed to solve my issue. I did this by using the solution you provided. 


  **Step By Step Instructions**


  Firefox Shortcut Right Click > ? Shortcut Editor > Desktop Entry > Command > Change The Code To: firefox /full/path/to/yourfile.html > Copy Edited Firefox Shortcut >  Go to:  ~/.config/autostart > Paste Edited Firefox Shortcut Into Folder > Restart PC

  To get full screen I just installed the add-on you mentioned in your last post. 


  Thanks for all your support
Kind Regards,
Paul

---

### Post by mcduck on 2015-05-01
Good to hear that you got it working!

---

