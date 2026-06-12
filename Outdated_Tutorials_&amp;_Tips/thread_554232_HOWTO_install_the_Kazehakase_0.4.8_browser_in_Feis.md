---
title: "HOWTO install the Kazehakase 0.4.8 browser in Feisty using the Fedora .rpm"
date: 2007-09-18
forum: Outdated Tutorials &amp; Tips
---

### Post by quixotic-cynic on 2007-09-18
This is a small note on how to install the latest version of Kazehakase (0.4.8 at this time) via a method other than compile (since the compile is not usually straight forward). The Kazehakase (KH) version in the Ubuntu repos is (very) outdated - thus the need for this guide.

[B]
What it is[/B]
From wikipedia:>  Kazehakase (&#39080;&#21338;&#22763;) is a web browser for Unix-like operating systems that uses the GTK+2 libraries. Like Galeon, Skipstone, and Epiphany, Kazehakase embeds the Gecko layout engine. However, the author also plans to add the ability to switch between different rendering engines (e.g. GtkHTML, Gtk+ WebCore, Dillo, w3m).

KH appears to be less resource intensive than the majority of current browsers, yet has more features than Dillo, Links2, etc, and thus offers a useful mid-point. about:config works.

**Main install**
```
mkdir ~/kazehakase
cd ~/kazehakase
wget http://koji.fedoraproject.org/packages/kazehakase/0.5.4/4.fc9/i386/kazehakase-0.5.4-4.fc9.i386.rpm
sudo aptitude install alien
sudo alien -i ./kazehakase-0.5.4-4.fc9.i386.rpm
```

Note: The above code is for the latest i386 version (@2008-04-30). Additional versions can be found at [http://koji.fedoraproject.org/packages/kazehakase/0.5.4/](http://koji.fedoraproject.org/packages/kazehakase/0.5.4/).

**Get gecko files with firefox installed**
Kazehakase also requires the use of an external rendering engine (gecko at present). These engine files appear to be required in the /usr/lib/kazehakase directory. To resolve this you can use the commands below (providing you have firefox installed). The files may also be available in other gecko-based browser directories in /usr/lib/

```

sudo cp /usr/lib/firefox/components /usr/lib/kazehakase/components -R
sudo cp /usr/lib/firefox/*.so /usr/lib/kazehakase

```
[B]
Get gecko files without installing firefox[/B] 
```

mkdir ~/ff-deb
cd ~/ff-deb
wget http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.6+1-0ubuntu1_i386.deb
ar -x *.deb
tar -xvzf data.tar.gz
sudo cp ./usr/lib/firefox/components /usr/lib/kazehakase -R
sudo cp ./usr/lib/firefox/*.so /usr/lib/kazehakase
```

**To undo**

```

sudo aptidute remove kazehakase
sudo aptitude remove alien
sudo rm -R /usr/lib/kazehakase/
```

**Info on commands**
If you do not understand what one of the commands is actually doing type *man <command>* in a terminal for an explanation, where <command> is the one you would like to find out about, e.g. sudo or aptitude or cp. See [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/) for more info. Lines beginning with sudo are those that can cause a lot of damage if they are typed or written incorrectly - please ensure they make sense.

**Notes**
* I cannot provide (much) support, please use at your own risk (though I will help if I can).
* This HOWTO was done using Feisty Fawn 7.04. Edit: Still applicable for 7.10 and any version thereafter in which the .rpm file is more up to date than the .deb file (Hardy etc).
* I discovered about alien at [http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/](http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/).
* Requires an .rpm of kazehakase 0.4.8 and the alien package.

---

### Post by fuscia on 2007-09-19
you have mixed versions in your instructions.


edit: it seems faster than the version in the repos.

---

### Post by quixotic-cynic on 2007-09-19
> **fuscia said:**
> you have mixed versions in your instructions.

Thanks. I changed the faulty line mentioning kazehakase-0.4.7 to *sudo alien -i ./kazehakase-0.4.8-1.fc7.i386.rpm* as it should be.

---

### Post by el mariachi on 2007-09-19
> **fuscia said:**
> you have mixed versions in your instructions.


edit: it seems faster than the version in the repos.
Have you compared it to Epiphany? Is it noticeable?

---

### Post by quixotic-cynic on 2007-09-19
Opened up each browser on this page then left for 10 minutes. These are the (approximate) resource usages via ps -aux. I have 768mb of memory. Of course, it has been said that unused ram is wasted ram (but I cant help myself).

```

%CPU %MEM    COMMAND
0.5  5.1   /usr/bin/galeon
0.5  5.0   /usr/bin/epiphany
0.9  4.9   /usr/lib/firefox/firefox-bin
0.7  4.8   kazehakase
0.6  4.4   /usr/local/iceweasel-2.0.0.6-g2-i386/iceweasel-bin
0.8  0.8   rxvt
0.0  0.7   /usr/bin/links2 -g

```

I find KH loads faster than the others (excluding links2 -g obviously). Epiphany is quite quick (though not good wrt resources?) but not as fast at loading as KH (and I just cant stand it's menu-for-dummies approach). Iceweasel seems to load fast too (how?!?) and I am suprised at it's results above (when compared with firefox).

---

### Post by K.Mandla on 2007-09-19
As an added bonus, a lot of the "speed tweaks" for Firefox that float around the Internet work for KH too.

[http://kmandla.wordpress.com/2007/08/25/kazehakase-on-steroids/](http://kmandla.wordpress.com/2007/08/25/kazehakase-on-steroids/)

---

### Post by Polygon on 2007-09-22
i tried this and when i try to enter a URL and press enter, it seg faults....... any ideas?

---

### Post by quixotic-cynic on 2007-09-22
> **Polygon said:**
> i tried this and when i try to enter a URL and press enter, it seg faults....... any ideas?

Did you copy the required files into the /usr/lib/kazehakase directory (see above)? The seg fault is usually what happens when it can't find the gecko engine.

I would suggest you check that the files that should have been copied are actually there (through the terminal and ls or a file manager like nautillus or thunar. Which method did you use to get the files - from the .deb or copied from the FF directory? Either way, the most effective way to check you have all the files is to compare with the /usr/lib/firefox directory of a working FF version - you should have the 'components' folder and any files ending in .so. I could post a file list if you need it.

---

### Post by Polygon on 2007-09-22
yeah i did, and i checked and there are folders and .so files in the /usr/lib/kazehakase folder

and when i start the program, it actually stars and appears to work, its only when i type something in the bar that it dies =/

i can edit the preferences and stuff and open the bookmarks, but as soon as it loads anything it dies..... hmm

---

### Post by quixotic-cynic on 2007-09-23
That was exactly the behaviour I had before I copied the files across - as soon as I entered any web address or clicked any link it seg faulted. Copying the files resolved it perfectly for me. I can't help that much more (because my knowledge is finite on this subject) but I will post a list of files on the off chance there is a discrepancy. Btw - I take it you have firefox 2.0.0.6 (I should have said that is the version I used I guess). If you have a different version it suggests another thing to check.

Here are the files that I have:

```
corcorigan@deidre:/usr/lib/kazehakase$ ls
components	 libgtkembedmoz.so  libmozjs.so		libxpcom.so
libgfxpsshar.so  libgtkxtbin.so     libxpcom_compat.so	libxpistub.so
libgkgfx.so	 libjsj.so	    libxpcom_core.so

corcorigan@deidre:/usr/lib/kazehakase/components$ ls
accessibility-atk.xpt	libbrowsercomps.so		 nsDictionary.js
accessibility.xpt	libbrowserdirprovider.so	 nsExtensionManager.js
alerts.xpt		libcaps.so			 nsFilePicker.js
appshell.xpt		libchrome.so			 nsHelperAppDlg.js
appstartup.xpt		libcommandlines.so		 nsInterfaceInfoToIDL.js
autocomplete.xpt	libcomposer.so			 nsMicrosummaryService.js
autoconfig.xpt		libcookie.so			 nsProgressDialog.js
bookmarks.xpt		libdocshell.so			 nsProxyAutoConfig.js
browsercompsbase.xpt	libeditor.so			 nsResetPref.js
browser-feeds.xpt	libembedcomponents.so		 nsSafebrowsingApplication.js
browsersearch.xpt	libfileview.so			 nsSearchService.js
caps.xpt		libgfx_gtk.so			 nsSearchSuggestions.js
chardet.xpt		libgfxps.so			 nsSessionStartup.js
chrome.xpt		libgklayout.so			 nsSessionStore.js
commandhandler.xpt	libgkplugin.so			 nsSetDefaultBrowser.js
commandlines.xpt	libhtmlpars.so			 nsSidebar.js
composer.xpt		libi18n.so			 nsUpdateService.js
content_base.xpt	libimglib2.so			 nsUrlClassifierLib.js
content_htmldoc.xpt	libjar50.so			 nsUrlClassifierListManager.js
content_html.xpt	libjsd.so			 nsUrlClassifierTable.js
content_xmldoc.xpt	libmork.so			 nsURLFormatter.js
content_xslt.xpt	libmozfind.so			 nsXmlRpcClient.js
content_xtf.xpt		libmyspell.so			 oji.xpt
cookie.xpt		libnecko2.so			 passwordmgr.xpt
directory.xpt		libnecko.so			 pipboot.xpt
docshell.xpt		libnsappshell.so		 pipnss.xpt
dom_base.xpt		liboji.so			 pippki.xpt
dom_canvas.xpt		libpermissions.so		 plugin.xpt
dom_core.xpt		libpipboot.so			 prefetch.xpt
dom_css.xpt		libpipnss.so			 pref.xpt
dom_events.xpt		libpippki.so			 profile.xpt
dom_html.xpt		libpref.so			 progressDlg.xpt
dom_loadsave.xpt	librdf.so			 proxyObjInst.xpt
dom_range.xpt		libremoteservice.so		 rdf.xpt
dom_sidebar.xpt		libsearchservice.so		 safebrowsing.xpt
dom_storage.xpt		libspellchecker.so		 satchel.xpt
dom_stylesheets.xpt	libstoragecomps.so		 saxparser.xpt
dom_svg.xpt		libsystem-pref.so		 search.xpt
dom_traversal.xpt	libtoolkitcomps.so		 sessionstore.xpt
dom_views.xpt		libtransformiix.so		 shellservice.xpt
dom_xbl.xpt		libtxmgr.so			 shistory.xpt
dom_xpath.xpt		libuconv.so			 spellchecker.xpt
dom.xpt			libucvmath.so			 storage.xpt
dom_xul.xpt		libuniversalchardet.so		 toolkitprofile.xpt
downloads.xpt		libwebbrwsr.so			 toolkitremote.xpt
editor.xpt		libwebsrvcs.so			 txmgr.xpt
embed_base.xpt		libwidget_gtk2.so		 txtsvc.xpt
extensions.xpt		libxmlextras.so			 uconv.xpt
exthandler.xpt		libxpcom_compat_c.so		 unicharutil.xpt
fastfind.xpt		libxpconnect.so			 update.xpt
FeedConverter.js	libxpinstall.so			 uriloader.xpt
FeedProcessor.js	locale.xpt			 url-classifier.xpt
feeds.xpt		lwbrk.xpt			 urlformatter.xpt
FeedWriter.js		microsummaries.xpt		 webBrowser_core.xpt
filepicker.xpt		migration.xpt			 webbrowserpersist.xpt
find.xpt		mimetype.xpt			 WebContentConverter.js
gfx.xpt			mozbrwsr.xpt			 webshell_idls.xpt
gksvgrenderer.xpt	mozfind.xpt			 websrvcs.xpt
history.xpt		necko_about.xpt			 widget.xpt
htmlparser.xpt		necko_cache.xpt			 windowds.xpt
imglib2.xpt		necko_cookie.xpt		 windowwatcher.xpt
inspector-cmdline.js	necko_data.xpt			 xml-rpc.xpt
inspector.xpt		necko_dns.xpt			 xpcom_base.xpt
intl.xpt		necko_file.xpt			 xpcom_components.xpt
jar.xpt			necko_ftp.xpt			 xpcom_ds.xpt
jsconsole-clhandler.js	necko_http.xpt			 xpcom_io.xpt
jsconsole.xpt		necko_res.xpt			 xpcom_obsolete.xpt
jsdservice.xpt		necko_socket.xpt		 xpcom_threads.xpt
layout_base.xpt		necko_strconv.xpt		 xpcom_xpti.xpt
layout_printing.xpt	necko_viewsource.xpt		 xpconnect.xpt
layout_xul_tree.xpt	necko.xpt			 xpinstall.xpt
layout_xul.xpt		nsBookmarkTransactionManager.js  xulapp.xpt
libaccessibility.so	nsBrowserContentHandler.js	 xuldoc.xpt
libappcomps.so		nsBrowserGlue.js		 xultmpl.xpt
libauth.so		nsCloseAllWindows.js
libautoconfig.so	nsDefaultCLH.js

```

I hope that helps somehow.

---

### Post by johnraff on 2007-11-24
Unfortunately that fedora download link just redirects to the Fedora 8 home page now.
A Google search came up with this list of kazehakase .rpms:
[http://rpm.pbone.net/index.php3?stat=3&limit=1&srodzaj=3&dl=40&search=kazehakase](http://rpm.pbone.net/index.php3?stat=3&limit=1&srodzaj=3&dl=40&search=kazehakase)

Any idea which one might work (if any ???)...

---

### Post by quixotic-cynic on 2007-11-24
Thanks for letting me know. I updated the instructions and it should work now.

---

### Post by johnraff on 2007-11-26
Cheers.
I'll have a go tomorrow when I'm awake... :)

<the next day>
Ahh... shame, the installation seemed to go OK but it won't start up for me.
I get this error in the terminal:
```
kazehakase: symbol lookup error: /usr/lib/kazehakase/libkazehakase.so.0: undefined symbol: g_once_init_enter_impl
```
Any ideas?

---

### Post by yotama9 on 2007-11-30
Hi all.

I just discovered KH this morning (the gutsy default version) and loved it.

I searched around and found that there is a new version and I tried to install it using your instructions.

all went well but I didn't noticed the cp part afterwards (and of course KH crashed every time). I rechecked the forums and in did, there was a missing part. I copied the file as instructed (I have firefox installed, as well as iceape) and retried running KH only to get the following errors:

```
(kazehakase:6393): Gtk-WARNING **: RubyDialog: missing action RubyDialog

(kazehakase:6393): Gtk-WARNING **: ReloadRuby: missing action ReloadRuby

(kazehakase:6393): Gtk-WARNING **: InstallAsRubyExtension: missing action InstallAsRubyExtension
Segmentation fault (core dumped)

```

I'm pretty sure I have ruby installed (check in synaptic) and I don't know what is wrong.

can you please help me?

Yotam

---

### Post by yotama9 on 2007-12-01
can anybody help me with it?

searching Google for that kind of problem didn't give much help :(

thanks.

---

### Post by koolkatkiwi on 2008-04-29
> **K.Mandla said:**
> As an added bonus, a lot of the "speed tweaks" for Firefox that float around the Internet work for KH too.

[http://kmandla.wordpress.com/2007/08/25/kazehakase-on-steroids/](http://kmandla.wordpress.com/2007/08/25/kazehakase-on-steroids/)

Hi. I did those tweaks that you mention, or something very similar, that I found on the internet. I can't find the page now, but it looked like an official page. After I did the tweaks, the browser would no longer open at all, so I'm now in the process of finding and installing another browser. I've learned my lesson about believing what someone says to do to your configuration files.

I tried Dillo first, after Kazehakase got stuffed. Boy, I don't want to use *THAT* browser again! It's painful. I'm off to try Swiftfox if I can figure out how to install it. (I'm using Fluxbuntu on an old laptop.)

Cheers,
Kath.

---

### Post by quixotic-cynic on 2008-04-30
Kath,

If the config is at fault then just deleting it will fix the problem - you'll have to enter your preferred options again but the browser would work:

rm ~/.kazehakase/mozilla/kazehakase/prefs.js

If that doesn't work and kazehakase is still broken then I guess the easiest thing to do is purge it (sudo aptitude purge kazehakase) and reinstall.

---

