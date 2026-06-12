---
title: "Themes that work with GS 3.2 and theme that don't work"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sanderd17 on 2011-10-05
Hi, I'm going to make an alphabetical list of themes that work in Gnome Shell 3.2, and themes that cause issues like this: [http://ubuntuforums.org/showthread.php?p=11302242](http://ubuntuforums.org/showthread.php?p=11302242)

**Working**

[LIST]
[*]Adwaita
[*]Adwaita Slim
[*]Elementary Luna
[*]ElementaryViper Luna
[*]Malys
[*]Metalx
[*]Nord
[*]Pantheon
[*]Zukitwo
[/LIST]

**Not working**
[LIST]

[*]Adwaita White
[*]Capazul
[*]DevianArt
[*]Drakfire Caffe
[*]Faience
[*]Gaia
[*]Google Shell
[*]Smooth Inset
[*] Old Steampunk
[*] Star Trek 
[*] Viper
[/LIST]

If you find other themes, please share.

---

### Post by dino99 on 2011-10-05
which ppa installed ?

---

### Post by sanderd17 on 2011-10-05
No ppa, just the most recent version of the themes available from the original source (gnomelook.org, devainart ...)

---

### Post by viper200 on 2011-10-05
First plz read my reply to your comment on metalx [http://justviper.deviantart.com/art/Metal-X-gnome-3-2-compatible-256652412](http://justviper.deviantart.com/art/Metal-X-gnome-3-2-compatible-256652412) and secondly have you tried this one [http://justviper.deviantart.com/art/ElementaryViper-Luna-shell-261144492](http://justviper.deviantart.com/art/ElementaryViper-Luna-shell-261144492)

---

### Post by sanderd17 on 2011-10-05
Thanks, I corrected it

---

### Post by viper200 on 2011-10-05
thanks

---

### Post by pilpul on 2011-10-10
for me (11.10 RC) Zukitwo does not work. Nord ([http://0rax0.deviantart.com/art/GNOME-Shell-Nord-214295138](http://0rax0.deviantart.com/art/GNOME-Shell-Nord-214295138)) does

---

### Post by sanderd17 on 2011-10-10
Nord indeed works, I added it, but Zukitwo also works for me. I use the most recent version from devianart.

---

### Post by tista on 2011-10-10
Mine works:
[https://launchpad.net/~tista/+archive/gtk3]("https://launchpad.net/~tista/+archive/gtk3")

Regards.

---

### Post by jbicha on 2011-10-10
I've not tried alternative GNOME Shell themes but I've received several reports about the Activities overview search freezing up with certain themes so check that the search works in these themes please.

---

### Post by BigCityCat on 2011-10-10
I have had numerous problems with nord.

---

### Post by sanderd17 on 2011-10-11
> **jbicha said:**
> I've not tried alternative GNOME Shell themes but I've received several reports about the Activities overview search freezing up with certain themes so check that the search works in these themes please.

Yes, I check that issue. Apart from that issue (and a little pixel shift in the top bar), all themes work.

@tista: where can I find your gnome shell theme archive.

@Bigcitycat: can you install a new version of the GS theme Nord? And what version of GS are you using? My version is 3.2.0. Everything works here.

---

### Post by VinDSL on 2011-10-11
> **tista said:**
> Mine works:
[https://launchpad.net/~tista/+archive/gtk3]("https://launchpad.net/~tista/+archive/gtk3")

Regards.
Yes, it does.

Thank you!  ;)

---

### Post by tista on 2011-10-11
> **sanderd17 said:**
> Yes, I check that issue. Apart from that issue (and a little pixel shift in the top bar), all themes work.

@tista: where can I find your gnome shell theme archive.

@Bigcitycat: can you install a new version of the GS theme Nord? And what version of GS are you using? My version is 3.2.0. Everything works here.

Hi sanderd17,

Mine is deb package on my PPA.
Direct Link is here:
[https://launchpad.net/~tista/+archive/gtk3/+files/gnome-shell-theme-pantheon_3.2.0-0ubuntu1%7Etista27_all.deb]("https://launchpad.net/~tista/+archive/gtk3/+files/gnome-shell-theme-pantheon_3.2.0-0ubuntu1%7Etista27_all.deb")

I didn't publish any source tarball yet...

cheers.

---

### Post by tista on 2011-10-11
> **VinDSL said:**
> Yes, it does.

Thank you!  ;)

You're welcome, VinDSL. ;)
And mine has gdm-shell theme as well! lol
[gdm 3.2 preview 1]("http://4.bp.blogspot.com/-RebHwpPxlyA/TpLnxs3M7dI/AAAAAAAAAG0/gvq5wAlsGFs/s1600/gdm.png")
[gdm 3.2 preview 2]("http://2.bp.blogspot.com/-O5o2f4ijNzQ/TpLn-UlOaVI/AAAAAAAAAG4/pXxYd24UYR8/s1600/gdm_2.png")

But today automatic install didn't succeed, so you should rename the default theme directory "/usr/share/gnome-shell/theme" to theme.org or something like that, and then make symlink from my theme located "/usr/share/themes/gnome-shell-pantheon/gnome-shell" to "/usr/share/gnome-shell/theme"...

Because today gdm 3.2 always watch that path only...

cheers.

---

### Post by sanderd17 on 2011-10-11
While the file is called pantheon, the theme (if I look at the gnome tweak tool, which uses the json file) is called Elementary Luna.

Is there a difference between your theme and the original Elementary Luna theme by Half-Left?

Maybe it would be better to change the name in the json file.

And thanks for the GDM tip. I'll have to look into this.

---

### Post by tista on 2011-10-11
> **sanderd17 said:**
> While the file is called pantheon, the theme (if I look at the gnome tweak tool, which uses the json file) is called Elementary Luna.

Is there a difference between your theme and the original Elementary Luna theme by Half-Left?

Maybe it would be better to change the name in the json file.

And thanks for the GDM tip. I'll have to look into this.

Really?
debian installation process may use the name of "gnome-shell-pantheon" for gnome-tweak-tool... :S

And yeah my code base was half-left's one. so I would rewrite json...

cheers.

---

### Post by sanderd17 on 2011-10-11
If you've fixed that small issue, please tell me. I'm gonna package it for Arch.

And the theme itself looks good and works. So I added it to the list of working themes already.

---

### Post by tista on 2011-10-11
> **sanderd17 said:**
> If you've fixed that small issue, please tell me. I'm gonna package it for Arch.

And the theme itself looks good and works. So I added it to the list of working themes already.

OK... finished build on LP:
[https://launchpad.net/~tista/+archive/gtk3/+files/gnome-shell-theme-pantheon_3.2.0-0ubuntu1%7Etista28_all.deb]("https://launchpad.net/~tista/+archive/gtk3/+files/gnome-shell-theme-pantheon_3.2.0-0ubuntu1%7Etista28_all.deb")

And diff is here:
[https://launchpadlibrarian.net/82536156/gnome-shell-theme-pantheon_3.2.0-0ubuntu1~tista27_3.2.0-0ubuntu1~tista28.diff.gz]("https://launchpadlibrarian.net/82536156/gnome-shell-theme-pantheon_3.2.0-0ubuntu1~tista27_3.2.0-0ubuntu1~tista28.diff.gz")

Thanks. ;)

---

### Post by sanderd17 on 2011-10-11
Thanks.

It's added to the AUR: [https://aur.archlinux.org/packages.php?ID=53069](https://aur.archlinux.org/packages.php?ID=53069)

---

