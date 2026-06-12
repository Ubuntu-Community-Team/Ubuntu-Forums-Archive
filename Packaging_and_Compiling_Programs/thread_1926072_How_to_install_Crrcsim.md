---
title: "How to install Crrcsim"
date: 2012-02-15
forum: Packaging and Compiling Programs
---

### Post by jbb1996 on 2012-02-15
How do you install Crrcsim [http://crrcsim.berlios.de/wiki/]("http://crrcsim.berlios.de/wiki/")
I have tried ever thing I can find and It still will not install

HELP ](*,)

---

### Post by Rodney9 on 2012-02-15
It is quite old, it's made for Etch version 8.04, we are now up to 11.10.

You will have dependencies problems as it will want to use old libs etc.

here are other flight sims to consider - 

[http://linux.about.com/od/softgame/a/swflightsims.htm](http://linux.about.com/od/softgame/a/swflightsims.htm)

Rodney

---

### Post by RMJ on 2012-06-01
Hi there, I know you asked this a few months ago but I found these instructions and installed it and it runs on 12.04! @Rodney, those flight sims are ok but are not trying to simulate flying model planes like CRRCsim. These are the instructions I used, also I had to install a compiler first (sudo apt-get install build-essential checkinstall), I'm no expert but this worked for me,


sudo apt-get install libsdl-dev
sudo apt-get install libplib-dev
sudo apt-get install portaudio19-dev
sudo apt-get install libjpeg-dev
Extract the CRRCsim file and in a terminal cd to the extracted files then:
./autogen.sh
./configure
make
sudo make install

Once finished type crrcsim and it should run in a window, enjoy :)

Jason

---

### Post by nick1221 on 2012-08-23
How do you do this: "Extract the CRRCsim file and in a terminal cd to the extracted files then:"

---

### Post by Toz on 2012-08-23
> **nick1221 said:**
> How do you do this: "Extract the CRRCsim file and in a terminal cd to the extracted files then:"

Note that the link in the first post is no longer active. The new location for CRRCsim is [http://sourceforge.net/apps/mediawiki/crrcsim/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/crrcsim/index.php?title=Main_Page").

Based on the source code download package from that site - crrcsim-0.9.12.tar.gz - from a terminal you would:
```
cd /location/of/crrcsim-0.9.12.tar.gz
tar xzvf crrsim-0.9.12.tar.gz
cd crrsim-0.9.12
```

You could also double-click the file and use the gui application to extract the files then use the terminal to cd into that location.

---

### Post by RMJ on 2012-08-24
> **nick1221 said:**
> How do you do this: "Extract the CRRCsim file and in a terminal cd to the extracted files then:"

Hi Nick,

As Toz described you can open it using the Terminal or double click on the file will open the GUI to extract it. The next operations have to be done in the Terminal though and you need to navigate to where the files have been extracted using the cd command, I had them in my Downloads folder so for me it was:

```
cd /home/jason/Downloads/Crrcsim-0.9.12/
```

note: use the TAB key to auto complete folder names

Hope this helps 

J

---

### Post by nick1221 on 2012-09-06
Ok I got to the part where it says "make"

I get this error: make: *** No targets specified and no makefile found.  Stop.

Any ideas on how to correct this?

---

### Post by projectbronco on 2013-07-18
I know this is an older thread, but it was very helpful, thanks! Crrcsim is awesome! Hopefully it will save me from crashing my real RC plane...

---

### Post by MikeCyber on 2014-01-10
Compiling in 13.04 I get:

michael@michael-Ubuntu:~/crrcsim-0.9.12$ make
 cd . && /bin/bash /home/michael/crrcsim-0.9.12/missing --run automake-1.11 --foreign
locale/Makefile.am:5: `localedir' is not a legitimate directory for `DATA'
make: *** [Makefile.in] Error 1
michael@michael-Ubuntu:~/crrcsim-0.9.12$ 

any help? Thanks

---

### Post by Toz on 2014-01-10
*Moved to **Packaging & Compiling** programs.*

> **MikeCyber said:**
> Compiling in 13.04 I get:

michael@michael-Ubuntu:~/crrcsim-0.9.12$ make
 cd . && /bin/bash /home/michael/crrcsim-0.9.12/missing --run automake-1.11 --foreign
locale/Makefile.am:5: `localedir' is not a legitimate directory for `DATA'
make: *** [Makefile.in] Error 1
michael@michael-Ubuntu:~/crrcsim-0.9.12$ 

any help? Thanks
[This site](http://translate.google.ca/translate?hl=en&sl=it&u=http://www.davidea.it/modellismo-elettrico/67-simulatore-di-volo-aeromodelli-per-linux.html%3Fshowall%3D1%26limitstart%3D&prev=/search%3Fq%3Dcrrcsim%2B%2560localedir%2527%2Bis%2Bnot%2Ba%2Blegitimate%2Bdirectory%2Bfor%2B%2560DATA%2527%26client%3Dubuntu%26hs%3DhXz%26channel%3Dfs%26biw%3D869%26bih%3D637) (translated) suggests that the version of automake is at issue. On 13.10 with Automake version 1.13.3 it works fine. The site suggests installing a different version of automake.

---

### Post by chris1379 on 2014-01-26
When I tried to follow the instructions I got what is pasted below. Notice the line:
locale/Makefile.am:5: `localedir' is not a legitimate directory for `DATA'
What does this mean?

me@mycomputer:~/Downloads/crrcsim-0.9.12$ ./autogen.sh
Removing old aclocal.m4...
Running autoheader...
Running aclocal...
Running automake...
locale/Makefile.am:5: `localedir' is not a legitimate directory for `DATA'
Running autoconf...

--------------------------------------------
Success, now you're ready to run ./configure
--------------------------------------------

---

### Post by Toz on 2014-01-26
The answer is in the last post, #10. Specifically, [this link]("http://translate.google.ca/translate?hl=en&sl=it&u=http://www.davidea.it/modellismo-elettrico/67-simulatore-di-volo-aeromodelli-per-linux.html%3Fshowall%3D1%26limitstart%3D&prev=/search%3Fq%3Dcrrcsim%2B%2560localedir%2527%2Bis%2Bnot%2Ba%2Blegitimate%2Bdirectory%2Bfor%2B%2560DATA%2527%26client%3Dubuntu%26hs%3DhXz%26channel%3Dfs%26biw%3D869%26bih%3D637").

---

### Post by chris1379 on 2014-01-29
Thanks, I got it to install using an older version of automake.

---

### Post by rossmort on 2014-09-17
> **chris1379 said:**
> Thanks, I got it to install using an older version of automake.

How exactly did you downgrade? I am trying via elementary (precise) and somehow blew things up. I lost my mouse pointer and file menus somehow....

---

