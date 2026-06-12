---
title: "Utopia fonts - how?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by dynamethod on 2008-07-27
Hi there im trying to install the Utopia font, heres my dpkg log of some texlive packages i installed, but still no luck!

```
2008-07-28 02:50:58 status unpacked texlive-base 2007-13
2008-07-28 02:50:58 status unpacked texlive-base 2007-13
2008-07-28 02:50:58 status unpacked texlive-base 2007-13
2008-07-28 02:50:58 status half-configured texlive-base 2007-13
2008-07-28 02:51:00 status installed texlive-base 2007-13
2008-07-28 02:51:00 configure texlive-fonts-recommended 2007-13 2007-13
2008-07-28 02:51:00 status unpacked texlive-fonts-recommended 2007-13
2008-07-28 02:51:00 status unpacked texlive-fonts-recommended 2007-13
2008-07-28 02:51:00 status half-configured texlive-fonts-recommended 2007-13
2008-07-28 02:51:01 status installed texlive-fonts-recommended 2007-13

```

help much appreciated

---

### Post by Vivaldi Gloria on 2008-07-27
I think texlive-fonts-recommended contains utopia fonts. I haven't used them myself so I'm not sure. Have you looked at this:

[http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=free-math-font-survey](http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=free-math-font-survey)

[http://ctan.tug.org/tex-archive/info/Free_Math_Font_Survey/](http://ctan.tug.org/tex-archive/info/Free_Math_Font_Survey/)
(alternative link)

---

### Post by ramjet_1953 on 2008-07-27
I have found that the easiest way to install a font is to use Nautilus in sudo mode.

If you go here:

[http://www.urbanfonts.com/free-fonts.htm](http://www.urbanfonts.com/free-fonts.htm)

You will find your font listed.

Just download the Windows version of the font and save it to a convenient location.

Next, unzip the archive by [COLOR="Blue"]right clicking on it[/COLOR] and select [COLOR="Blue"]extract here[/COLOR].
If there is only one file, it will just extract it in the same directory. However if there is more than one file, it will create a sub-directory and extract there.

Next do this:

Open a terminal and type this code into it:

```
gksu nautilus
``` 

After entering your login password Nautilus will open in sudo mode.

Now, navigate to [COLOR="Blue"]/home/<your home>/<location of file you unzipped>
[/COLOR]
Right-click on the ttf file and [COLOR="Blue"]select copy[/COLOR].

Navigate to [COLOR="Blue"]/usr/share/fonts/truetype[/COLOR].

Right-click on the truetype folder and select [COLOR="Blue"]create folder[/COLOR]

When the window opens type [COLOR="Blue"]utopia[/COLOR] into the name field and close it.

Now right click on the newly-created utopia folder and click [COLOR="Blue"]paste into folder[/COLOR].

Done! Now when you open your word processor, your new font should be available.

Regards,
Roger :cool:

---

### Post by dynamethod on 2008-07-28
Thanks very much for the replys, but it seems from that web link that i have to buy these fonts, is there an open source alternative to the Utopia font?

---

### Post by ramjet_1953 on 2008-07-28
If you go here:

[http://www.urbanfonts.com/fonts/fonts-U.htm](http://www.urbanfonts.com/fonts/fonts-U.htm)

Utopia appears to be listed as a freebie.

Regards,
Roger :cool:

---

### Post by dynamethod on 2008-07-28
Ah ok, this is strange, the Utopia font im looking for is the same font thats within this conky script here: 

[http://ubuntuforums.org/showpost.php?p=5464823&postcount=843](http://ubuntuforums.org/showpost.php?p=5464823&postcount=843)

The Utopia font listed in [http://www.urbanfonts.com/fonts/fonts-U.htm](http://www.urbanfonts.com/fonts/fonts-U.htm) doesnt appear to be the same i think.

But thanks heaps for the installation tips!

---

### Post by btate on 2008-07-28
Did as described above until I tried to navigate to /user/share/fonts/truetype

Seems I don't have a font folder at all. being a total newbie to this I'm probably missing a key ingredient :) direction would be appreciated.

Bt

---

### Post by dynamethod on 2008-07-28
> **btate said:**
> Did as described above until I tried to navigate to /user/share/fonts/truetype

Seems I don't have a font folder at all. being a total newbie to this I'm probably missing a key ingredient :) direction would be appreciated.

Bt

its **/usr/share/fonts/truetype**, you have /**user**/share/fonts/truetype

small typo

---

### Post by Elfy on 2008-07-28
I put them in my home - .fonts

Then I don't lose them when I reinstall

---

### Post by Vivaldi Gloria on 2008-07-28
dynamethod,

I thought you were trying to use the utopia fonts with latex, that's why I directed you to latex fonts guide above.

Now I see that you only want to use it in regular programs. To do that put the font in

```
/usr/share/fonts/truetype
```

or 

```
~/.fonts
```

as mentioned above and then rebuild the font cache:

```
sudo fc-cache -f -v
```

---

### Post by sagemintblue on 2011-01-29
I had a similar question, though I needed Utopia fonts to use the LaTeX Fourier-GUT math font package:

[http://www.tug.dk/FontCatalogue/utopia/](http://www.tug.dk/FontCatalogue/utopia/)
[http://www.ctan.org/tex-archive/fonts/fourier-GUT/](http://www.ctan.org/tex-archive/fonts/fourier-GUT/)

Solution is to grab the Utopia tex font distribution here:

[http://www.ctan.org/tex-archive/fonts/utopia/](http://www.ctan.org/tex-archive/fonts/utopia/)

Then proceed with instructions within Fourier-GUT.

---

