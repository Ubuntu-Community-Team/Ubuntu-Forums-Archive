---
title: "Problem Installing &quot;Restricted Extras&quot; in 16.04"
date: 2016-05-08
forum: New to Ubuntu
---

### Post by kraus37043 on 2016-05-08
Apps usually take a minute or two to install.  I tried to install Restricted Extras from the software center and the terminal.  The installation proceeded smoothly and then hung up when it reached the Microsoft fonts.  I waited almost 3 hours before giving up.  I tried the installation Saturday morning.  Would another time be better?

Also, is there a way to determine if Ubuntu is hung up or just slow?

---

### Post by Dennis N on 2016-05-08
I believe there is a EULA* you need to OK before the install proceeds on those fonts. Try again and keep an eye out for it.

*end user license agreement

---

### Post by RobGoss on 2016-05-08
Hello and welcome, I know you stated that you also installed **Ubuntu restricted Extras** from the software center and you waited about three hours but how about when you tried from your terminal did this method also take three hours? 

When installing the Ubuntu Restricted Extras are installed you would not be able to see it because it runs in the background and will install all the packages needed to help your desktop perform as needed


Is this the terminal command you used to install the Ubuntu restricted Extras

Try this code:

```
[COLOR=#111111][FONT=Consolas]sudo apt-get install ubuntu-restricted-extras[/FONT][/COLOR] 
```

I find it odd that it would take that long to install this not saying that you are not correct, what kind of connection are you using to access the internet?

---

### Post by him610 on 2016-05-08
> there is a EULA* you need to OK before the install proceeds on those fonts. Try again and keep an eye out for it.

Oftentimes, you might find it hiding underneath all of your open windows.

---

### Post by Geoffrey_Arndt on 2016-05-08
+1 for him610 and Dennis N.   This is a known problem - - usually can see the EULA window if you minimize the installer windows.   What a PITA.

---

### Post by wildmanne39 on 2016-05-08
> **Dennis N said:**
> I believe there is a EULA* you need to OK before the install proceeds on those fonts. Try again and keep an eye out for it.

*end user license agreementIndeed this is the case, a dialog window appears in the terminal you need to use the TAB and arrow keys to navigate the options and ENTER to ultimately select the desired option. 

They can be installed from the terminal if needed.
```
sudo apt-get install ubuntu-restricted-extras
```
or
```
sudo apt-get update
```
Then:
```
sudo apt-get install ttf-mscorefonts-installer
```if you just want to install micrsoft fonts by themselves.

Watch for the window, you may have to look under other open windows to find it.
Thanks

---

### Post by kraus37043 on 2016-05-08
I saw the Eula, but was not aware that the "button" to accept was hiding.  I clicked on the word "OK", but it was not a live link.  Thanks for the suggestion.

---

### Post by wildmanne39 on 2016-05-08
It does not work if you click on it you have to highlight it with the tab key and possibly arrow keys then hit enter.

---

### Post by vasa1 on 2016-05-08
> **kraus37043 said:**
> Apps usually take a minute or two to install.  I tried to install Restricted Extras from the software center **and the terminal**.  The installation proceeded smoothly and then hung up when it reached the Microsoft fonts.  I waited almost 3 hours before giving up.  I tried the installation Saturday morning.  Would another time be better?

Also, is there a way to determine if Ubuntu is hung up or just slow?

So OP **has already tried** the terminal approach.

---

### Post by mc4man on 2016-05-09
Slightly Ot- users should be advised to install ubuntu-restricted-addons instead of ubuntu-restricted-extras as it generally provides all they're looking for without the  ttf-mscorefonts.. that aren't all that useful.

---

### Post by kraus37043 on 2016-05-09
Thanks to all who offered suggestions.  Special thanks to wild man who informed me that I need to use the TAB key to highlight  OK and YES.

---

### Post by wildmanne39 on 2016-05-09
Your welcome! Please use normal fonts when posting except where allowed according to:
> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.
[http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)

---

### Post by kraus37043 on 2016-05-09
Thanks to all who offered suggestions.  Special thanks to wild man who informed me that I need to use the[SIZE=5] [SIZE=6]TAB[/SIZE][/SIZE][SIZE=5] key to highlight  [/SIZE]OK[SIZE=2] and[/SIZE][SIZE=6]YES[/SIZE][SIZE=6].[/SIZE]

---

### Post by vasa1 on 2016-05-10
It would be nice if you mark the thread [SOLVED]! Here's how: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

