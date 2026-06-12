---
title: "changing system wide fonts"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by cylent on 2013-12-05
because i am to read in Arabic the fonts that come with Ubuntu are literally crap.

so i watched a video that linked to a download and it showed to put the folder and rename it to .fonts in your home folder. 
it worked for the Firefox fonts and everything looked great.

however -- system wide as in ubuntu itself when displaying arabic still looked "old style".

how can the fonts folder be installed to be used system wide? 

(fonts folder contains fonts from Microsoft fonts -+ others making a collection of 239 fonts)

---

### Post by ajgreeny on 2013-12-05
All the fonts you will use in Ubuntu are stored in two places.

1.  /usr/share/fonts
2.  ~/.fonts

I recommend you install them in the #1 location as if you install them to your /home directory they will not be accessible from another user account on the computer, including the system utilities you speak of.

First make a folder to hold your custom fonts.```
sudo mkdir /usr/share/fonts/truetype/myfonts
```  I am using myfonts as an example.

Next open a terminal in the folder where you have a bunch of custom fonts and type the following:```
sudo cp ./*.ttf /usr/share/fonts/truetype/myfonts
```  This will copy the truetype fonts to that folder.  You may need to do this separately for any named fonts where the file suffix .TTF is in upper case, as linux is case sensistive.

Now that we have the fonts in the proper folder we need to install them in Ubuntu.  That is what the fc-cache command is for.

Open a terminal in your myfonts folder and type the following:```
sudo fc-cache -f -v
```

This will install the fonts so that both your applications like OpenOffice and other users can use them.

I hope this helps.

---

