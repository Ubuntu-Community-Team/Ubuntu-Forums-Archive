---
title: "My font installation experience (Ubuntu 14.04)"
date: 2016-05-27
forum: New to Ubuntu
---

### Post by Jeff_Rockel on 2016-05-27
Greetings, I hope this post helps others avoid the experience I had. I recently changed 100% from Windows to Linux (OK, I still watch Netflix under Windows on a VM under Linux) and am using Ubuntu 14.04 with LibreOffice 4.2. I wanted to install some new fonts. Found the font I wanted online and downloaded the .ttf file. I double clicked on the .ttf file and Font Viewer 3.8 popped up. I clicked the install button, reloaded Libre Draw and the font was not found. Here is why:

Font view installed the font to Home/.local/share/fonts
Through some other forum links, I found there were about a half dozen places fonts could reside including: /usr/share/fonts/... which is where the Libre core fonts were stored in variously named folders.

After continued searching I found that by placing the .ttf files in Home/.fonts they would be visible to Libre (and I suppose other applications). NOTE: If you are in a terminal, Home is represented with ~. So copy to ~/.fonts

Thank you so much for allowing me to participate. I hope to continue contributing to the community as I find thing helpful to me. :D

---

### Post by howefield on 2016-05-28
> **Jeff_Rockel said:**
> ...(OK, I still watch Netflix under Windows on a VM under Linux) and am using Ubuntu 14.04 with LibreOffice 4.2. I wanted to install some new fonts.

Just for info, Netflix plays with Chrome in Linux, just mentioning in case you were unaware.

> Now, for my question to Linux developers.

If you seriously want to attract the attention of the developers, you really need to file a bug. These forums are user based, Ubuntu users helping other Ubuntu users and so, are probably not the best placed venue to get your point across to your intended audience.

---

### Post by Jeff_Rockel on 2016-05-28
howefield, Thanks for the note on chrome. I did install it and had issues first time around. I then found [this thread]("http://ubuntuforums.org/showthread.php?t=2293262") that fixed the issue. All-in-all there isn't anything I can't find a solution for in Ubuntu.

---

### Post by Jorhel on 2016-06-10
I ran into the same problem this afternoon and here is another solution that I found elsewhere on the forums.

"First make a system folder to hold your custom fonts.

```
sudo mkdir /usr/share/fonts/truetype/myfonts 
```

I am using myfonts as an example.
Next open a terminal in the folder where you have a bunch of custom fonts and run command

```
sudo cp ./*.ttf /usr/share/fonts/truetype/myfonts
```

This will copy the truetype fonts to that folder. You may need to do this separately for any named fonts where the file suffix .TTF is in upper case, as linux is case sensistive.
Now that we have the fonts in the proper folder we need to install them in Ubuntu. Run command

```
sudo fc-cache -f -v

```
This will install the fonts so that both your applications like LibreOffice, and any other users including the system utilities can use them."

I also installed .otf fonts by repeating the same processe but creating a OTF folder
```
sudo mkdir /usr/share/fonts/OTF/myfonts
```

then using ```
sudo cp ./*.otf /usr/share/fonts/OTF/myfonts
``` 

Worked a treat.

---

### Post by Jeff_Rockel on 2016-06-11
Jorhel, Thanks for the useful info. My observations are that after the copy, fc-cache finds both locations (usr/share/fonts and /home/jeff/.fonts where I copied from). I don't think it makes any difference, just something I noticed as the text flew by. 

I agree 100% that "fc-cache" is the tool required to get all fonts made available to linux programs. I think ~/.fonts is a magic location to linux (at least fc-cache) since it scanned that location. I also agree that copying to /usr/share/fonts... ensures new fonts are found by fc-cache.
Jeff

---

