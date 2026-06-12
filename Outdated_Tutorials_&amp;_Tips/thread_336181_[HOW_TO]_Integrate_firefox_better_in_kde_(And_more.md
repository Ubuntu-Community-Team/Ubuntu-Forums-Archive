---
title: "[HOW TO] Integrate firefox better in kde? (And more, little optimizations)"
date: 2007-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by MetaMorfoziS on 2007-01-11
Hi all!
I'm just gonna write down, how to:
- Get nice form widgets
- Get a more usable/nicer gui
- Get KDE dialogs in firefox (instead the very unusable one)
- resize "web developer toolbar" (In 1024*768)
- set up colorzilla on a firefox that is installed from package
Before start: My english grammar is very poor, basically i'm hungarian. :rolleyes: 

I'm hacked this out on kubuntu edgy, but i think it works on every platform, if you:
- Know where is your firefox (and have write permission over it) (/usr/lib/firefox by default) (else: `**whereis firefox**`)
- Know where is your firefox settings directory (~/.mozilla) :)


[SIZE=4]It looks like[/SIZE]
This [**_Before_**]("http://metamorfozis.hu/p/ff_before.png") and [**_After_**]("http://metamorfozis.hu/p/ff_after.png")

[SIZE=4]Form widgets[/SIZE]
As you can see, the default forms that firefox renders is not too nice (disgusting).
The solution is pretty easy, i found that [here]("http://dnite.wordpress.com/2006/10/28/pretty-widgets-for-firefox-for-linux/").

You need to download [a tarball]("http://home.comcast.net/%7Etehdnite/linux/prettywidgets_firefox2_linux.tar.gz") with some css and pngs, then extract it to your firefox install direcotory.

```

cd
wget http://home.comcast.net/~tehdnite/linux/prettywidgets_firefox2_linux.tar.gz
sudo cp -r /usr/lib/firefox/res/ /usr/lib/firefox/res_original  # backing up
tar -xvvzf prettywidgets_firefox2_linux.tar.gz
sudo mv ./prettywidgets_firefox2_linux/* /usr/lib/firefox/res/

```Then, restart firefox, and enjoy the first step of this how to.

**UPDATE:** I have found a newer solution, that works better for me, so check out that: 
[http://ubuntuforums.org/showthread.php?t=369596](http://ubuntuforums.org/showthread.php?t=369596)
I recommend this more than the above stated because it's select dropdown has a border, that is a big problem with the old one and in some pages, the old widgets just shows a button without text. 
So thank you for the good work fatsheep.



[SIZE=4]GUI improvement[/SIZE]
You only need to fire up your favourite editor, and open your userChrome.css:

```

kate ~/.mozilla/firefox/<your profile blabla>/chrome/userChrome.css

```Then, add what you want from the following:
```

/* 
1, You can roundize or polarize your URL bar, with the setting of the -moz-border-radious's value (0 is square)
*/
#urlbar {
-moz-appearance: none !important;
-moz-border-radius: 0px !important;
padding-right: 1px !important;
}

/* 
2, With this, you can hide the little close buttons on the tabs
*/
.tab-close-button {
display: none !important;
}

/* 
3, Multi column Bookmarks
*/
#bookmarks-ptf {display:block}
#bookmarks-ptf toolbarseparator {display:inline}

/* 
4, We can set the transparency of the current selected tab
*/
#content tab:not([selected="true"]) {
-moz-opacity: 0.8 !important;
} 

/* 
5, With this you can remove the little "history" arrows from the Back/Forrward buttons on the url bar
*/
.toolbarbutton-menubutton-dropmarker {
display: none !important;
}


``````

/* 
**6, This is my favourite: ** With this, you can resize your search field. If you move your mouse over the search bar, the right-side search-glass button is disappar, and the field gets bigger.
*/
#search-container {
width: 10px !important;
max-width: 10px !important;
}
#search-container:hover {
width: 200px !important;
max-width: 200px !important;v padding: 0px 5px 0px 0px;
}
#search-container:hover .search-go-button-stack {
display: none !important;
}

```[SIZE=4]KDE dialogs in firefox[/SIZE]
This is a hacky solution that under construction, but it works. Sometimes it does crazy things, but that is very rare and possible only for me:)

So you need to set up this: [http://kde-apps.org/content/show.php?content=36077](http://kde-apps.org/content/show.php?content=36077)
There is a topic in ubuntuforums, where i found it as [a package]("http://www.insulae.com.ar/tmp/kgtk/kgtk_0.8-1_i386.deb"), but i'm not found actually that topic. (If you found, please tell me)

So when you have setupped kgt, do the folowing:

```

sudo mv /usr/bin/firefox /usr/bin/firefoxy
kdesu kate /usr/bin/firefox # open kate, or your favourite editor to create the new firefox link
[code]
Then copy and paste this:
[code]
#!/bin/sh
/usr/local/kde/bin/kgtk-wrapper firefoxy $@

```Save and close, then:
```

sudo chmod +x /usr/bin/firefox # set it to executable

```Restart firefox, and enjoy.

[SIZE=4]Resize the web developer toolbar [/SIZE]
([More about WDT]("https://addons.mozilla.org/firefox/60/"))

If you have 1024*768 or lower resolution, this toolbar hangs out on the right side of the window. We can easily solve this with renaming some of the long menu names.

- Information -> Infz
- Miscellaneous -> Misc
- View Source -> View src
And what you want...

To do it, go  to your mozilla settings directory, and find out your webdeveloper.jar

Mine is here: /home/meta/.mozilla/firefox/twnfkn8g.default/extensions/
{c45c406e-ab73-11d8-be73-000a95be3b12}/chrome/webdeveloper.jar

Then just simply enter to it, and find the following file:
... /locale/en-US/webdeveloper/main.dtd
(This is a compressed file, in krusader you just need to press enter, and you can browse it,i'm not tried, but it think the same in konqueror, but you able to uncompress it, find and do the changes on the file and recompress it...)

Open it (F4 in my example) and edit what you want.
[IMG]http://metamorfozis.hu/p/webdev.png[/IMG]
Then save, and close it. Restart firefox and enjoy:)

[SIZE=4]Set up colorzilla[/SIZE]
([More about colorzilla]("https://addons.mozilla.org/firefox/271/"))

If you have firefox from package, from the official repos, actually you can't use this extension, i dunno why. So if you want to get it working you need to [**_get_**]("http://getfirefox.com") the original and latest firefox, and copy all of the libxpcom* files to your /usr/lib/firefox. Then reinstall colorzilla and restart firefox and enjoy and make long sentences and with too much and and thats all folks, i hope it helps.

---

### Post by Extreme Coder on 2007-01-16
Great guide! The widget trick is new to me, it is now bearable to look at Firefox!
Anyway, the page in the Gentoo wiki has some neat tricks too.
[http://gentoo-wiki.com/HOWTO_Integrate_Firefox_with_KDE](http://gentoo-wiki.com/HOWTO_Integrate_Firefox_with_KDE)


Extreme Coder

---

### Post by userundefine on 2007-02-20
> **MetaMorfoziS said:**
> If you have firefox from package, from the official repos, actually you can't use this extension, i dunno why. So if you want to get it working you need to [**_get_**]("http://getfirefox.com") the original and latest firefox, and copy all of the libxpcom* files to your /usr/lib/firefox. Then reinstall colorzilla and restart firefox and enjoy and make long sentences and with too much and and thats all folks, i hope it helps.
Nice thread.

You can also use the color picker that comes with KDE by default and sits in your taskbar as an applet.  I prefer this because it's global and is easier to use.  Check it out.

Thanks for the FF widgets trick!

---

### Post by TheWizzard on 2007-02-21
[http://konquefox.free.fr/](http://konquefox.free.fr/)

---

### Post by userundefine on 2007-02-21
Nice link, wizzard!

---

### Post by ingo on 2007-11-12
Very useful stuff here. However, what exactly does ```
kdesu kate /usr/bin/firefox # 
```do?

---

