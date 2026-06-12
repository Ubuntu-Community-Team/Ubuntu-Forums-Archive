---
title: "Packaging and deplying Python application"
date: 2008-11-17
forum: Programming Talk
---

### Post by Tony Flury on 2008-11-17
I am in the final stages of developing and testing a python application (using GTK) that allows you to upload pictures to flickr (yes i did get the API to work after actually reading the docs).


Its features include : 
[LIST=1]
[*]Multiple flickr accounts
[*]Pictures displayed as thumbnails
[*]Double click on pictures to show full size in viewer
[*]Multiple selection of pictures
[*]Adding of tags and sets to selected pictures even when multiple pics are selected.[*]Creation of new flickr sets directly from the Gui
[*]Uploading of pictures, with titles, tags and sets to flickr.
[/LIST]

Still to be added : 
[LIST=1]
[*]Picture description
[*]Picture permissions and Licences
[*]User preferences including :
[LIST=a]
[*]optional default account to start on
[*]optional starting folder to load pictures from - per user
[*]optional tags to add to pictures - per user
[*]optional automatic title based on file name - per user
[*]optional automatic tags and sets based on file location - per user
[*]alternative image viewer selection - per user
[*]default permissions and Licences
[/LIST]
[*]Documentation
[*]Readme's etc
[/LIST]

future wish list - v2.0 and beyond - vanity tools
[LIST=1]
[*]Tool to build "most viewed" set with one click
[*]Build "most commented" sets with one click
[*]Build "most favorited" set with one click
[/LIST]

Once i finish the application (to v1.0) I would like to include the whole thing as a package and make it available for others to use if they wish - what is the best way of doing that.

Also : what do people recommend for providing on-line help within the application ?

---

### Post by pmasiar on 2008-11-17
> **Tony Flury said:**
> include the whole thing as a package and make it available for others to use if they wish - what is the best way of doing that.

ez_install egg

> what do people recommend for providing on-line help within the application ?

mailing list (free at google groups) and wiki (free at wikidot (I like it more) or pbwiki - see my sig)

Edit: google code provides easier-to-use features than SF, including wiki, if you want also host code repository

---

### Post by nanotube on 2008-11-17
> **pmasiar said:**
> 
mailing list (free at google groups) and wiki (free at wikidot (I like it more) or pbwiki - see my sig)

or host it on sourceforge, and get mailing list, wiki, website, cvs/svn, file release hosting, and a few other things, for free. :)

---

### Post by bobbocanfly on 2008-11-17
Or a mix between SF and Google Code: Launchpad. Bug tracker, answers tracker, translations tracker, Specifications tracker, Bazaar hosting, package archive, mailing lists.

Not as complex/feature-full as sourceforge, but not as basic as Google code.

---

### Post by Sorivenul on 2008-11-17
> **bobbocanfly said:**
> Or a mix between SF and Google Code: Launchpad. Bug tracker, answers tracker, translations tracker, Specifications tracker, Bazaar hosting, package archive, mailing lists.

Not as complex/feature-full as sourceforge, but not as basic as Google code.

As a member of SourceForge and Launchpad, I vastly prefer Launchpad.  That may be because I now prefer Bazaar to either SVN or CVS.

---

### Post by loell on 2008-11-17
> **Tony Flury said:**
> 
Once i finish the application (to v1.0) I would like to include the whole thing as a package and make it available for others to use if they wish - what is the best way of doing that.

another howto: [Making a deb package out of a python script.]("http://www.showmedo.com/videos/video?name=linuxJensMakingDeb&fromSeriesID=37")

---

### Post by Tony Flury on 2008-11-18
ok - and how is the best way to package a help file - or is the best way to go with on line help, and launch a browser ?

---

### Post by bobbocanfly on 2008-11-18
> **Tony Flury said:**
> ok - and how is the best way to package a help file - or is the best way to go with on line help, and launch a browser ?

If you are debian packaging it, add all the documentation you want to install to debian/docs and add a call to dh_installdocs in your debian/rules binary-arch target.

---

### Post by Tony Flury on 2008-11-18
Thank you to everyone for your replies. 

I think i have a long way to go before i grok most if any of what was said.

I will have another read in a day or so :-)

---

