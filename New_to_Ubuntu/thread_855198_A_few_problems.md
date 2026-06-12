---
title: "A few problems"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Oreo Killa 225 on 2008-07-10
Hello.

I started dual-booting Vista and Ubuntu about a week ago. I have already decided to make Ubuntu my main O/S. However there is one problem that keeps annoying me. In Firefox, the font characters are too close together. Any help with that?

Also, when going to pages that have this in the source:

```
<embed src="yourmusicfile.mid" autostart="true" loop="true"
width="2" height="0">
</embed>
<noembed>
<bgsound src="yourmusicfile.mid" loop="infinite">
</noembed>
```

It says I need to install a missing plugin, but then says the plugin can not be found. So I decided to download the RealPlayer plugin. However it is a .bin file, does anyone know how to install said file?

Thanks, and any help is appreciated.

---

### Post by roquefilipe on 2008-07-10
from [http://www.w3schools.com/media/media_browsersounds.asp](http://www.w3schools.com/media/media_browsersounds.asp) :

> The <bgsound> element is not a standard HTML or XHTML element. It is supported by Internet Explorer only.
maybe this is the reason it does not work in firefox ?

---

### Post by Oreo Killa 225 on 2008-07-10
> **roquefilipe said:**
> from [http://www.w3schools.com/media/media_browsersounds.asp](http://www.w3schools.com/media/media_browsersounds.asp) :


maybe this is the reason it does not work in firefox ?

Nah, it works on Firefox in Vista. I just need the right plugin, which is a .bin file, which I don't know how to install.

---

### Post by fatality_uk on 2008-07-10
If you look in FireFox preferences, Under the content tab, you can define more clearly the fonts used in FF.

**bgsound** is IE specific.

The site authour would need to use embed instead.

---

### Post by Oreo Killa 225 on 2008-07-10
> **fatality_uk said:**
> If you look in FireFox preferences, Under the content tab, you can define more clearly the fonts used in FF.

**bgsound** is IE specific.

The site authour would need to use embed instead.

There is both **embed** and **bgsound**. The code successfully works on Opera, Firefox, and IE. But that's not the point. I just need to know how to install a .bin file as a FF plugin. Also the font direction you lead me in your post, doesn't help with the character spacing.

---

### Post by Troll_the_Great on 2008-07-10
Here is a link who could help you install things in Ubuntu:\
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
Hope that helps.
Cheers!

---

### Post by fatality_uk on 2008-07-10
Navigate to where you have the *.bin file located using the terminal. Once in the correct directory, type

> sudo chmod +x RealPlayerFile_name.bin
Then type
> ./RealPlayer11GOLD.bin
And it should give you instructons, I imagne!!! I don't have RP on my system, but that should install a bin

---

### Post by Oreo Killa 225 on 2008-07-10
> **fatality_uk said:**
> Navigate to where you have the *.bin file located using the terminal. Once in the correct directory, type


Then type

And it should give you instructons, I imagne!!! I don't have RP on my system, but that should install a bin


hmmm. Tried that yesterday, but didn't know what directory to install it in. I tried /usr/lib/firefox/plugins, but it didn't work. So where should it be?

---

### Post by fatality_uk on 2008-07-10
If you type into a terminal
> find /home -name '*.bin'
It will list all the *.bin files you have in your home directory, or which ever directry you specify. Then grab the path to realplayer.bin and use that

---

### Post by Oreo Killa 225 on 2008-07-10
No. When installing RealPlayer, it asks me which directory do I want install it in. Where do I install it if I want it as a Firefox plugin?

---

### Post by fatality_uk on 2008-07-10
Here's the links you need I think:

[https://help.ubuntu.com/community/FirefoxPlugins#Real%20Player](https://help.ubuntu.com/community/FirefoxPlugins#Real%20Player)

[https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealplayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealplayerInstallationMethods)

> To make Firefox 2 call RealPlayer for realaudio / video files, go to Edit > Preferences > Content > File Types > Manage.... Select the "real audio" file type and click "Change action.." Check the setting for "Open with the default application" (unless you have made changes to this setting previously, it will probably say Totem). If you want the file to open with an external program other than the default (like RealPlayer), select "Open with this application" - you will then be prompted to select an application. Navigate to the start-up script for RealPlayer ("realplay") located in the "RealPlayer" program folder. The location will differ depending on the installation method you have chosen. For a typical install using the installer from the RealNetworks web site, it will be

> /usr/local/RealPlayer/realplay

---

### Post by Oreo Killa 225 on 2008-07-10
aww damn.

I found the problem. I wrote the wrong URL in the source.
Ok, anyways.

What about the character spacing?

---

### Post by fatality_uk on 2008-07-10
So you followed my instructions for RealPlayer?

To be clear. The character spacing in FireFox is effecting **ALL** web sites you visit? If so, post a screenshot of FireFox

---

### Post by Oreo Killa 225 on 2008-07-10
It only does it on some websites.

Here's the screenshot:

```
http://img247.imageshack.us/img247/3006/screenshot1pu6.png
```

---

### Post by Oreo Killa 225 on 2008-07-10
Anyone?

---

### Post by fatality_uk on 2008-07-10
To my eye, there looks nothing wrong with that screenshot! The fonts are proportional. Other than it's a slightly odd resolution 1440x900, which I assume is the screen res you have Ubuntu set to.

Change your screen resolution and try revisiting that web site and see if it looks the same.

---

### Post by Oreo Killa 225 on 2008-07-10
> **fatality_uk said:**
> To my eye, there looks nothing wrong with that screenshot! The fonts are proportional. Other than it's a slightly odd resolution 1440x900, which I assume is the screen res you have Ubuntu set to.

Change your screen resolution and try revisiting that web site and see if it looks the same.

It's not the font in white, it's the font in bold light blue. (the forum titles)

---

### Post by fatality_uk on 2008-07-10
It's the sites <font> or CSS definition. It's not FireFox!!

---

### Post by Oreo Killa 225 on 2008-07-10
*deleted*

---

