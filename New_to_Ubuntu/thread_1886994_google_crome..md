---
title: "google crome."
date: 2011-11-26
forum: New to Ubuntu
---

### Post by vrpatilisl on 2011-11-26
hi
I downloaded google crome .deb from official website. it is not instaling. It open with software centre every time and install is highlighted everytime.
Thanxs

---

### Post by shashanksingh on 2011-11-26
Make sure it is the exact version that should work for you.
Check out the 32 bit and 64 bit options

---

### Post by T.exe on 2011-11-26
use the terminal installation.. (the deb package must be present in the current directory your terminal is pointing to!)

[B]sudo dpkg -i *packagename*.deb


[/B]

---

### Post by vrpatilisl on 2011-11-26
pointed in same directory?
Consider package on desktop then what is command. The version of pakage is accurate.

---

### Post by lolpenguin on 2011-11-26
```
sudo apt-get install chromium-browser
```
It is the open-source version of Chrome, it gets updated a bit later, but is essentially the same.

---

### Post by T.exe on 2011-11-26
> **vrpatilisl said:**
> pointed in same directory?
Consider package on desktop then what is command. The version of pakage is accurate.

By default the terminal is pointed to the 'Home'directory...

Type in **pwd** to check which directory you're currently in.

To change from home to Desktop, type in
**cd ~/Desktop**

To check the files present in the current directory, type the command **ls** in the terminal.

---

### Post by T.exe on 2011-11-26
**@vrpatilisl**

Do try to get your hand on and learn Linux commands(highly recommended). 

Cheers! :)

---

### Post by doppel.ganger on 2011-11-26
You said it was on the desktop? Open a terminal:
```
sudo dpkg -i ~/Desktop/replace-with-name-of-file.deb
```
Then type in your password. It won't show up as you're typing it.

---

### Post by mhgsys on 2011-11-26
^ that 

+ likely you'll get some unmet dependencies

so.. after above do a ```
sudo apt-get install -f
``` and it will install during that process.

---

### Post by vrpatilisl on 2011-11-26
hi i tried terminal 
but password not typing i also tried to copy paste pass, still not worked.

---

### Post by doppel.ganger on 2011-11-26
Already explained. As you type it, it will not show up. Security measure. Just type your pass like normal, then hit enter. I guarantee it will work.

---

### Post by Spyderkid on 2011-11-26
[SIZE="3"][COLOR="Blue"]When you download it, double click on it, (or right click 'open with' 'ubuntu software centre') then Ubuntu software centre should open with the package displayed (GoogleChrome-stable, or something like that) then just click install...[/COLOR][/SIZE]
[COLOR="Red"]
If it doesn't work... Make sure you've downloaded the right .deb either the 32bit or the 64 bit
[/COLOR]

If it still doesn't work... Install Chromium from the software centre, (it's basically the same as Google Chrome)


[COLOR="Gray"]To install Chromium from command line use ```
 sudo apt-get install chromium 
```[/COLOR]

---

### Post by SavageWolf on 2011-11-26
Uh, installing it from the software centre should be the first thing tried, rather than all this messing around with Deb files.

Just go to the dash and type "Software Centre" (11.04+) or Select it from the applications menu, and then search for "Chrome".

---

### Post by JayKay3OOO on 2011-11-26
The chromium browser works the same as chrome so use that. All the chrome extensions and such work the same in chromium. You can even set up file sync in chrome and it will sync the same stuff to chromium so y'know.

Open software centre and search for chrome/chromium. Enter your password. Wait and use.

By the way. If you do use the terminal don't sudo apt-get install chromium as that will install a game called cromium.

The correct chromium package via terminal would be sudo apt-get install chromium-browser.

Hope this all helps you install chromium via software centre or terminal.

---

### Post by Spyderkid on 2011-11-27
> **SavageWolf said:**
> Uh, installing it from the software centre should be the first thing tried, rather than all this messing around with Deb files.

Just go to the dash and type "Software Centre" (11.04+) or Select it from the applications menu, and then search for "Chrome".

You can't install google chrome from the software centre...

Hence why there is this disscusion

---

### Post by SavageWolf on 2011-11-27
You can still install Chromium, which is more or less the same thing, there is no real reason to have Chrome over Chromium...

---

### Post by shashanksingh on 2011-11-27
Just curious.
Why is it named chromium in ubuntu? Why not chrome?

---

### Post by stracky on 2011-11-27
Yeah, the whole "terminal password" thing confused me the fist time too. 

In Windows, it shows *** instead of your password.  In terminal, it doesn't show anything at all!

Just type the password as you normally would and hit enter, it should work.

---

### Post by thetruckinglife on 2011-11-28
> **SavageWolf said:**
> You can still install Chromium, which is more or less the same thing, there is no real reason to have Chrome over Chromium...

i agree with this.
it will save you more headaches if you just use the software center and install Chromium browser.

---

### Post by vasa1 on 2011-11-28
> **SavageWolf said:**
> You can still install Chromium, which is more or less the same thing, there is no real reason to have Chrome over Chromium...
I guess, like so many things, the preference for Chrome or Chromium is personal. I prefer Chrome since I don't have "privacy issues" and Chrome comes with its own Flash and PDF reader.

---

### Post by clerisy on 2011-11-28
Check out the 32 bit and 64 bit options select which  version of system u have

---

### Post by Paqman on 2011-11-28
> **shashanksingh said:**
> Just curious.
Why is it named chromium in ubuntu? Why not chrome?

It's not just Ubuntu, you can get Chrome and Chromium for Windows and Mac too. Chromium is the open source version of Chrome that al the development gets done in. Google then take a snapshot of Chromium, bundle in some other bits and pieces and release it as Chrome.

The stable version of Chrome is a lot less flaky than Chromium in my experience, and as mentioned bundles some useful stuff. A lot of folks do like Chromium though, so it's up to you. 

The .deb from Google is the best way to install Chrome, as it'll also add the repository that you need to get updates.

---

### Post by T.exe on 2011-11-28
> **shashanksingh said:**
> Just curious.
Why is it named chromium in ubuntu? Why not chrome?

I too want to know the same! I believe 'Chromium' is how Canonical branded Chrome in Ubuntu, just as Debian brands Mozilla as 'IceWeasel' because of some proprietary issues.

correct me if i am wrong....

---

### Post by vasa1 on 2011-11-28
> **T.exe said:**
> I too want to know the same! I believe 'Chromium' is how Canonical branded Chrome in Ubuntu...
correct me if i am wrong....

Chromium is Chromium.

Chrome is Chrome.

Canonical does not brand Chrome as Chromium.

Chromium is available from the Ubuntu Software Center.

Chrome is available from [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) and, as part of the installation, it will set up its own ppa for updates.

---

### Post by shashanksingh on 2011-11-30
> **vrpatilisl said:**
> hi i tried terminal 
but password not typing i also tried to copy paste pass, still not worked.

Just a tit-bit.

When you copy paste on the terminal, its not just 
Ctrl+C or Ctrl+V

Its Ctrl+SHIFT+C/V

@vasa1 Thanks

---

### Post by Spyderkid on 2011-11-30
> **shashanksingh said:**
> Just a tit-bit.

When you copy paste on the terminal, its not just 
Ctrl+C or Ctrl+C

Its Ctrl+SHIFT+C/V

@vasa1 Thanks

or just use right-click & paste :)

---

### Post by drmrgd on 2011-11-30
> **Spyderkid said:**
> You can't install google chrome from the software centre...

Hence why there is this disscusion

But you could right click on the .deb file and choose open in Software Center.  Then when it loads, you can click the install button and it should install from there.  That might be way easier and intuitive for the OP.

---

### Post by Spyderkid on 2011-11-30
> **drmrgd said:**
> But you could right click on the .deb file and choose open in Software Center.  Then when it loads, you can click the install button and it should install from there.  That might be way easier and intuitive for the OP.

I meant by default, I said earlier that you can double click on it to open in the software centre.....

---

