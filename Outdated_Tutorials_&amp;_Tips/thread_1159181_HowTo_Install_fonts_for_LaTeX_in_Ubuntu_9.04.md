---
title: "HowTo: Install fonts for LaTeX in Ubuntu 9.04"
date: 2009-05-14
forum: Outdated Tutorials &amp; Tips
---

### Post by rplantz on 2009-05-14
This HowTo is for TeXLive on Ubuntu 9.04. It assumes that texlive is installed. It describes how to install the LuxiMono font for use with LaTeX. The concepts here should apply to other fonts.

LuxiMono is a nice font for program code listings in LaTeX. It is available at [www.ctan.org/tex-archive/fonts/LuxiMono/](www.ctan.org/tex-archive/fonts/LuxiMono/).

The important documents are:

a) TeX-on-Debian.* -- available in txt, pdf, and html in /usr/share/doc/tex-common/

b) README.luximono -- came with LuxiMono.

Here are the steps I followed (use sudo before each of the commands in this description to create a system-wide installation):

1. Download LuxiMono.zip and unzip it creating the LuxiMono directory, which contains the files referred to below.

2. Copy the file ul9.zip into the directory
```

       /usr/local/share/texmf/

```
   and unzip it.

3. Create the directory:
```

       /usr/local/share/texmf/fonts/type1/public/luxi

```
   and copy the .pfb files into it.
   
4. Create the directory:
```

       /usr/local/share/texmf/fonts/afm/public/luxi

```
   and copy the .afm files into it.
   
5. Move the directory
```

       /usr/local/share/texmf/dvips

```
   into the directory
```

       /usr/local/share/texmf/fonts/map/

```
   
   *Note:* Apparently the ul9.zip file was created for tetex2. Placement of .map files changed for TeXLive and tetex3. Section 4.3 in TeX-on-Debian states that the .map file should be located:
```

         /usr/local/share/texmf/fonts/map/dvips/luximono/ul9.map

```
   This step places it in:
```

         /usr/local/share/texmf/fonts/map/dvips/config/ul9.map

```
      which worked for me.
   
   If the directory
```

         /usr/local/share/texmf/fonts/map/dvips/config/

```
      already exists, simply move the file ul9.map into it.
   
6. Create the file
```

       /etc/texmf/updmap.d/10local.cfg

```
   which contains the line
```

       Map ul9.map

```
   If the file already exists, simply add the line to it.

7. (Picking up at step 3 in TeX-on-Debian) Run the program update-updmap.

8. Run the program mktexlsr.

9. Run the program updmap-sys.

---

### Post by samjam on 2009-08-20
[http://miknight.blogspot.com/2005/](http://miknight.blogspot.com/2005/) 11/how-to-install-luxi-mono-font-in.html suggests:

sudo updmap --enable MixedMap ul9.map


I found this to be essential, otherwise the luximono text showed up blank in my pdf.

(It still shows up nasty in my dvi)

---

### Post by knkillname on 2009-10-30
Ok, so here is the "for humans beings" way: Just open a terminal and type
```
sudo getnonfreefonts-sys --all
```
Done! :)

---

### Post by guendalf on 2011-02-24
@knkillname: Thanks! That's exactly what I'm looking for as I was getting boring to install these fonts manually.

---

### Post by kilmarnock on 2011-05-11
@knkillname: Thanks!

---

