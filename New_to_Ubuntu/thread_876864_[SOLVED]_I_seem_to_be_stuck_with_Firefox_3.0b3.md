---
title: "[SOLVED] I seem to be stuck with Firefox 3.0b3"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by staib on 2008-08-01
Hi all,
At some stage I downloaded beta 3 of Firefox 3.0, but despite seeing the odd Firefox 3.0 update since then I seem to be stuck with the beta version. Can some kind soul explain to me how I can either update or remove the beta version and then install the current version - it would be nice to keep my bookmarks...
Cheers,
Nick

---

### Post by t0p on 2008-08-01
A possibly stupid question: have you tried uninstalling the Firefox beta then installing the latest Firefox through Synaptic?

---

### Post by mikewhatever on 2008-08-01
Can you tell exactly how you installed firefox3b5.

---

### Post by staib on 2008-08-01
> **t0p said:**
> A possibly stupid question...
No such thing as a stupid question!
Rather confusingly Synaptic shows that I have Firefox 3.0.1 installed, but if I launch firefox from the file list (or from the terminal) it launches as 'Firefox 3 Beta 3' (and the Help/About in FF also says 3.0b3).

---

### Post by staib on 2008-08-01
> **mikewhatever said:**
> Can you tell exactly how you installed firefox3b5.
It was b3, but no, not entirely sure (not through Synaptic, though)...

---

### Post by faical117 on 2008-08-01
for the bookmarks you can find it here /home/yourname/.mozilla/firefox/???????.default

(delete it with synaptice manager or 'use apt-get remove firefox' and install new fresh one the [COLOR="Red"]firefox 3.0.1[/COLOR])

---

### Post by staib on 2008-08-01
> **faical117 said:**
> delete it with synaptice manager or 'use apt-get remove firefox' and install new fresh one the [COLOR="Red"]firefox 3.0.1[/COLOR])
Thanks guys.  I just used the apt-get remove firefox command and it seemed to work (freed up 123kb of disk space) - but I noticed that the ff icon remained (on the top bar) as did the menu item. Synaptic still showed 3.0.1 installed, so I removed that (using Synaptic).  That action also removed the icons and menu item. But (like the cat that came back) if I type firefox into the Terminal I still load up 3.0b3. How can I see where that one is and remove it?!

---

### Post by mikewhatever on 2008-08-01
> **staib said:**
> It was b3, but no, not entirely sure (not through Synaptic, though)...

It looks like you have two versions installed and need to get rid of the beta one. To do that, we need to know how it was installed.

> I just used the apt-get remove firefox command and it seemed to work (freed up 123kb of disk space)

No it didn't. Firefox takes a lot more space then 123kb.

---

### Post by staib on 2008-08-01
I know, I know - I should keep a log of everything - I suspect this was one of those guides on the net that I stumbled across and just couldn't resist ](*,)

Is there any way to discover where it is?  Or am I doomed to 3.0b3 for ever?!

---

### Post by kpkeerthi on 2008-08-01
Do you remember if you installed it using a .deb file?

---

### Post by staib on 2008-08-01
> **kpkeerthi said:**
> Do you remember if you installed it using a .deb file?
Possibly...  I'm sorry to sound like a klutz but I really can't recall the exact steps taken...  mind you, at my age (over 50) I sometimes can't remember the day of the week!

---

### Post by kpkeerthi on 2008-08-01
OK... Let me try. You need to run the commands in a terminal window.

1. Uninstall firefox3 you installed from repository
```
sudo aptitude purge firefox
```

2. Update your file catalog
```
sudo updatedb
```

3. Find where else is firefox lurking around
```
locate firefox
```

Post the output of the locate command here, preferably within [code] tags

---

### Post by staib on 2008-08-01
> **kpkeerthi said:**
> OK... Let me try. You need to run the commands in a terminal window.

1. Uninstall firefox3 you installed from repository
```
sudo aptitude purge firefox
```

2. Update your file catalog
```
sudo updatedb
```

3. Find where else is firefox lurking around
```
locate firefox
```

Post the output of the locate command here, preferably within ```
 tags

OK - 1 and 2 done.

3 - Output of locate command:

[code]/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/it-IT/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ja/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ja/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ja/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ja/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ja-JP/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ja-JP/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ja-JP/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ja-JP/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ko-KR/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ko-KR/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ko-KR/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ko-KR/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nb-NO/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nb-NO/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nb-NO/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nb-NO/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nl-NL/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nl-NL/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nl-NL/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nl-NL/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pl-PL/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pl-PL/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pl-PL/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pl-PL/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pt-BR/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pt-BR/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pt-BR/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pt-BR/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pt-PT/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pt-PT/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pt-PT/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/pt-PT/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ru-RU/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ru-RU/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ru-RU/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/ru-RU/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/sk-SK/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/sk-SK/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/sk-SK/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/sk-SK/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/tr-TR/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/tr-TR/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/tr-TR/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/tr-TR/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/uk-UA/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/uk-UA/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/uk-UA/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/uk-UA/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-CN/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-CN/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-CN/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-CN/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-TW/conflicts.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-TW/foxmarks.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-TW/foxmarks.properties
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-TW/setup.dtd
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/foxmarks.css
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/dirty.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/error.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/foxmarks-active.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/foxmarks-default.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/foxmarks-hover.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/foxmarks.ico
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/foxmarks.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/foxmarks_bug.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/pane-selector-advanced.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/pane-selector-bg-hover.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/pane-selector-bg-selected.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/pane-selector-bg.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/pane-selector-general.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/pane-selector-icons.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/pane-selector-macosx-bg-sel.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/pane-selector-macosx-bg.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/ready.png
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern/images/working.gif
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/components/foxmarks-service.idl
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/components/foxmarks-service.js
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/components/foxmarks-service.xpt
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/defaults/preferences
/home/dad/.mozilla/firefox/394ikf4w.default/extensions/foxmarks@kei.com/defaults/preferences/prefs.js
/home/dad/.mozilla/firefox/394ikf4w.default/minidumps/0290897a-575b-c9a3-667c920a-6c8071b0.dmp
/home/dad/.mozilla/firefox/394ikf4w.default/minidumps/0290897a-575b-c9a3-667c920a-6c8071b0.extra
/home/dad/.mozilla/firefox/Crash Reports/InstallTime2008020513
/home/dad/.mozilla/firefox/Crash Reports/LastCrash
/home/dad/.mozilla/firefox/Crash Reports/UserID
/home/dad/.mozilla/firefox/Crash Reports/crashreporter.ini
/home/dad/.mozilla/firefox/Crash Reports/pending
/home/dad/.mozilla/firefox/Crash Reports/submit.log
/home/dad/.mozilla/firefox/Crash Reports/pending/33b7a72d-f23a-1bd0-337f44da-2d807e77.dmp
/home/dad/.mozilla/firefox/Crash Reports/pending/33b7a72d-f23a-1bd0-337f44da-2d807e77.extra
/home/kyle/.icons/firefox-document.png
/opt/firefox
/opt/firefox/.autoreg
/opt/firefox/README.txt
/opt/firefox/Throbber-small.gif
/opt/firefox/application.ini
/opt/firefox/browserconfig.properties
/opt/firefox/chrome
/opt/firefox/components
/opt/firefox/crashreporter
/opt/firefox/crashreporter-override.ini
/opt/firefox/crashreporter.ini
/opt/firefox/defaults
/opt/firefox/dictionaries
/opt/firefox/extensions
/opt/firefox/firefox
/opt/firefox/firefox-bin
/opt/firefox/greprefs
/opt/firefox/icons
/opt/firefox/libfreebl3.chk
/opt/firefox/libfreebl3.so
/opt/firefox/libmozjs.so
/opt/firefox/libnspr4.so
/opt/firefox/libnss3.so
/opt/firefox/libnssckbi.so
/opt/firefox/libnssdbm3.so
/opt/firefox/libnssutil3.so
/opt/firefox/libplc4.so
/opt/firefox/libplds4.so
/opt/firefox/libsmime3.so
/opt/firefox/libsoftokn3.chk
/opt/firefox/libsoftokn3.so
/opt/firefox/libsqlite3.so
/opt/firefox/libssl3.so
/opt/firefox/libxpcom.so
/opt/firefox/libxul.so
/opt/firefox/modules
/opt/firefox/mozilla-xremote-client
/opt/firefox/old-homepage-default.properties
/opt/firefox/platform.ini
/opt/firefox/plugins
/opt/firefox/removed-files
/opt/firefox/res
/opt/firefox/run-mozilla.sh
/opt/firefox/searchplugins
/opt/firefox/updater
/opt/firefox/updater.ini

/opt/firefox/chrome/browser.jar
/opt/firefox/chrome/browser.manifest
/opt/firefox/chrome/classic.jar
/opt/firefox/chrome/classic.manifest
/opt/firefox/chrome/comm.jar
/opt/firefox/chrome/comm.manifest
/opt/firefox/chrome/en-US.jar
/opt/firefox/chrome/en-US.manifest
/opt/firefox/chrome/icons
/opt/firefox/chrome/pippki.jar
/opt/firefox/chrome/pippki.manifest
/opt/firefox/chrome/reporter.jar
/opt/firefox/chrome/reporter.manifest
/opt/firefox/chrome/toolkit.jar
/opt/firefox/chrome/toolkit.manifest
/opt/firefox/chrome/icons/default
/opt/firefox/chrome/icons/default/default16.png
/opt/firefox/chrome/icons/default/default32.png
/opt/firefox/chrome/icons/default/default48.png
/opt/firefox/components/FeedConverter.js
/opt/firefox/components/FeedProcessor.js
/opt/firefox/components/FeedWriter.js
/opt/firefox/components/WebContentConverter.js
/opt/firefox/components/browser.xpt
/opt/firefox/components/fuelApplication.js
/opt/firefox/components/jsconsole-clhandler.js
/opt/firefox/components/libbrowsercomps.so
/opt/firefox/components/libbrowserdirprovider.so
/opt/firefox/components/libdbusservice.so
/opt/firefox/components/libimgicon.so
/opt/firefox/components/libmozgnome.so
/opt/firefox/components/libnkgnomevfs.so
/opt/firefox/components/nsAddonRepository.js
/opt/firefox/components/nsBlocklistService.js
/opt/firefox/components/nsBrowserContentHandler.js
/opt/firefox/components/nsBrowserGlue.js
/opt/firefox/components/nsContentDispatchChooser.js
/opt/firefox/components/nsContentPrefService.js
/opt/firefox/components/nsDefaultCLH.js
/opt/firefox/components/nsDownloadManagerUI.js
/opt/firefox/components/nsExtensionManager.js
/opt/firefox/components/nsFilePicker.js
/opt/firefox/components/nsHandlerService.js
/opt/firefox/components/nsHelperAppDlg.js
/opt/firefox/components/nsLivemarkService.js
/opt/firefox/components/nsLoginInfo.js
/opt/firefox/components/nsLoginManager.js
/opt/firefox/components/nsLoginManagerPrompter.js
/opt/firefox/components/nsMicrosummaryService.js
/opt/firefox/components/nsPlacesTransactionsService.js
/opt/firefox/components/nsProxyAutoConfig.js
/opt/firefox/components/nsSafebrowsingApplication.js
/opt/firefox/components/nsSearchService.js
/opt/firefox/components/nsSearchSuggestions.js
/opt/firefox/components/nsSessionStartup.js
/opt/firefox/components/nsSessionStore.js
/opt/firefox/components/nsSetDefaultBrowser.js
/opt/firefox/components/nsSidebar.js
/opt/firefox/components/nsTaggingService.js
/opt/firefox/components/nsTryToClose.js
/opt/firefox/components/nsURLFormatter.js
/opt/firefox/components/nsUpdateService.js
/opt/firefox/components/nsUrlClassifierLib.js
/opt/firefox/components/nsUrlClassifierListManager.js
/opt/firefox/components/nsWebHandlerApp.js
/opt/firefox/components/pluginGlue.js
/opt/firefox/components/storage-Legacy.js
/opt/firefox/components/txEXSLTRegExFunctions.js
/opt/firefox/defaults/autoconfig
/opt/firefox/defaults/pref
/opt/firefox/defaults/profile
/opt/firefox/defaults/autoconfig/platform.js
/opt/firefox/defaults/autoconfig/prefcalls.js
/opt/firefox/defaults/pref/channel-prefs.js
/opt/firefox/defaults/pref/firefox-branding.js
/opt/firefox/defaults/pref/firefox-l10n.js
/opt/firefox/defaults/pref/firefox.js
/opt/firefox/defaults/pref/reporter.js
/opt/firefox/defaults/profile/bookmarks.html
/opt/firefox/defaults/profile/chrome
/opt/firefox/defaults/profile/localstore.rdf
/opt/firefox/defaults/profile/mimeTypes.rdf
/opt/firefox/defaults/profile/prefs.js
/opt/firefox/defaults/profile/chrome/userChrome-example.css
/opt/firefox/defaults/profile/chrome/userContent-example.css
/opt/firefox/dictionaries/en-US.aff
/opt/firefox/dictionaries/en-US.dic
/opt/firefox/extensions/inspector@mozilla.org
/opt/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/opt/firefox/extensions/inspector@mozilla.org/chrome
/opt/firefox/extensions/inspector@mozilla.org/chrome.manifest
/opt/firefox/extensions/inspector@mozilla.org/components
/opt/firefox/extensions/inspector@mozilla.org/defaults
/opt/firefox/extensions/inspector@mozilla.org/install.rdf
/opt/firefox/extensions/inspector@mozilla.org/platform
/opt/firefox/extensions/inspector@mozilla.org/chrome/inspector.jar
/opt/firefox/extensions/inspector@mozilla.org/components/inspector-cmdline.js
/opt/firefox/extensions/inspector@mozilla.org/defaults/preferences
/opt/firefox/extensions/inspector@mozilla.org/defaults/preferences/inspector.js
/opt/firefox/extensions/inspector@mozilla.org/platform/Linux
/opt/firefox/extensions/inspector@mozilla.org/platform/Linux/chrome
/opt/firefox/extensions/inspector@mozilla.org/platform/Linux/chrome/icons
/opt/firefox/extensions/inspector@mozilla.org/platform/Linux/chrome/icons/default
/opt/firefox/extensions/inspector@mozilla.org/platform/Linux/chrome/icons/default/winInspectorMain.xpm
/opt/firefox/extensions/inspector@mozilla.org/platform/Linux/chrome/icons/default/winInspectorMain16.xpm
/opt/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/opt/firefox/greprefs/all.js
/opt/firefox/greprefs/security-prefs.js
/opt/firefox/greprefs/xpinstall.js
/opt/firefox/icons/document.png
/opt/firefox/icons/mozicon128.png
/opt/firefox/icons/mozicon16.xpm
/opt/firefox/icons/mozicon50.xpm
/opt/firefox/modules/DownloadUtils.jsm
/opt/firefox/modules/ISO8601DateUtils.jsm
/opt/firefox/modules/JSON.jsm
/opt/firefox/modules/Microformats.js
/opt/firefox/modules/PluralForm.jsm
/opt/firefox/modules/XPCOMUtils.jsm
/opt/firefox/modules/distribution.js
/opt/firefox/plugins/flashplugin-alternative.so
/opt/firefox/plugins/libnullplugin.so
/opt/firefox/plugins/libtotem-basic-plugin.so
/opt/firefox/plugins/libtotem-basic-plugin.xpt
/opt/firefox/plugins/libtotem-gmp-plugin.so
/opt/firefox/plugins/libtotem-gmp-plugin.xpt
/opt/firefox/plugins/libtotem-mully-plugin.so
/opt/firefox/plugins/libtotem-mully-plugin.xpt
/opt/firefox/plugins/libtotem-narrowspace-plugin.so
/opt/firefox/plugins/libtotem-narrowspace-plugin.xpt
/opt/firefox/plugins/libunixprintplugin.so
/opt/firefox/res/EditorOverride.css
/opt/firefox/res/arrow.gif
/opt/firefox/res/arrowd.gif
/opt/firefox/res/broken-image.gif
/opt/firefox/res/charsetData.properties
/opt/firefox/res/charsetalias.properties
/opt/firefox/res/contenteditable.css
/opt/firefox/res/designmode.css
/opt/firefox/res/dtd
/opt/firefox/res/effective_tld_names.dat
/opt/firefox/res/entityTables
/opt/firefox/res/fonts
/opt/firefox/res/forms.css
/opt/firefox/res/grabber.gif
/opt/firefox/res/hiddenWindow.html
/opt/firefox/res/html
/opt/firefox/res/html.css
/opt/firefox/res/langGroups.properties
/opt/firefox/res/language.properties
/opt/firefox/res/loading-image.gif
/opt/firefox/res/mathml.css
/opt/firefox/res/quirk.css
/opt/firefox/res/svg.css
/opt/firefox/res/table-add-column-after-active.gif
/opt/firefox/res/table-add-column-after-hover.gif
/opt/firefox/res/table-add-column-after.gif
/opt/firefox/res/table-add-column-before-active.gif
/opt/firefox/res/table-add-column-before-hover.gif
/opt/firefox/res/table-add-column-before.gif
/opt/firefox/res/table-add-row-after-active.gif
/opt/firefox/res/table-add-row-after-hover.gif
/opt/firefox/res/table-add-row-after.gif
/opt/firefox/res/table-add-row-before-active.gif
/opt/firefox/res/table-add-row-before-hover.gif
/opt/firefox/res/table-add-row-before.gif
/opt/firefox/res/table-remove-column-active.gif
/opt/firefox/res/table-remove-column-hover.gif
/opt/firefox/res/table-remove-column.gif
/opt/firefox/res/table-remove-row-active.gif
/opt/firefox/res/table-remove-row-hover.gif
/opt/firefox/res/table-remove-row.gif
/opt/firefox/res/ua.css
/opt/firefox/res/unixcharset.properties
/opt/firefox/res/viewsource.css
/opt/firefox/res/dtd/mathml.dtd
/opt/firefox/res/dtd/xhtml11.dtd
/opt/firefox/res/entityTables/html40Latin1.properties
/opt/firefox/res/entityTables/html40Special.properties
/opt/firefox/res/entityTables/html40Symbols.properties
/opt/firefox/res/entityTables/htmlEntityVersions.properties
/opt/firefox/res/entityTables/mathml20.properties
/opt/firefox/res/entityTables/transliterate.properties
/opt/firefox/res/fonts/mathfont.properties
/opt/firefox/res/fonts/mathfontSTIXNonUnicode.properties
/opt/firefox/res/fonts/mathfontSTIXSize1.properties
/opt/firefox/res/fonts/mathfontStandardSymbolsL.properties
/opt/firefox/res/fonts/mathfontUnicode.properties
/opt/firefox/res/html/folder.png
/opt/firefox/searchplugins/amazondotcom.xml
/opt/firefox/searchplugins/answers.xml
/opt/firefox/searchplugins/creativecommons.xml
/opt/firefox/searchplugins/eBay.xml
/opt/firefox/searchplugins/google.xml
/opt/firefox/searchplugins/wikipedia.xml
/opt/firefox/searchplugins/yahoo.xml
/usr/bin/firefox
/usr/bin/mozilla-firefox
/usr/lib/firefox
/usr/lib/firefox-addons
/usr/lib/firefox/.autoreg
/usr/lib/firefox/extensions
/usr/lib/firefox/plugins
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome.manifest
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/install.rdf
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/uninstall
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome/en-GB.jar
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/uninstall/Uninstall
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/extensions/langpack-en-AU@firefox-3.0.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-CA@firefox-3.0.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.0.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.0.ubuntu.com/chrome
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.0.ubuntu.com/chrome.manifest
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.0.ubuntu.com/install.rdf
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.0.ubuntu.com/chrome/en-GB.jar
/usr/share/firefox
/usr/share/app-install/desktop/firefox-2.desktop
/usr/share/app-install/desktop/firefox-greasemonkey.desktop
/usr/share/app-install/desktop/firefox-launchpad-plugin.desktop
/usr/share/app-install/desktop/firefox-sage.desktop
/usr/share/app-install/desktop/firefox-showcase.desktop
/usr/share/app-install/desktop/firefox-themes-ubuntu.desktop
/usr/share/app-install/desktop/firefox-ubuntu-it-menu.desktop
/usr/share/app-install/desktop/firefox-webdeveloper.desktop
/usr/share/app-install/desktop/firefox.desktop
/usr/share/app-install/icons/firefox-greasemonkey.xpm
/usr/share/app-install/icons/firefox-launchpad-plugin.xpm
/usr/share/app-install/icons/firefox-sage.xpm
/usr/share/app-install/icons/firefox-showcase.xpm
/usr/share/app-install/icons/firefox-themes-ubuntu.xpm
/usr/share/app-install/icons/firefox-ubuntu-it-menu.png
/usr/share/app-install/icons/firefox-webdeveloper.xpm
/usr/share/apport/package-hooks/firefox.pyc
/usr/share/doc/mozilla-firefox-locale-en-gb
/usr/share/doc/mozilla-firefox-locale-en-gb/changelog.Debian.gz
/usr/share/doc/mozilla-firefox-locale-en-gb/copyright
/usr/share/firefox/defaults
/usr/share/firefox/defaults/pref
/usr/share/firefox/defaults/pref/apturl.js
/var/cache/apt/archives/firefox-3.0-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_i386.deb
/var/cache/apt/archives/firefox-3.0-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb
/var/cache/apt/archives/firefox-3.0_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_i386.deb
/var/cache/apt/archives/firefox-3.0_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb
/var/cache/apt/archives/firefox-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_all.deb
/var/cache/apt/archives/firefox-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_all.deb
/var/cache/apt/archives/firefox_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_all.deb
/var/cache/apt/archives/firefox_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_all.deb
/var/lib/mozilla-firefox
/var/lib/dpkg/alternatives/firefox-flashplugin
/var/lib/dpkg/info/firefox-3.0.list
/var/lib/dpkg/info/firefox-3.0.postrm
/var/lib/dpkg/info/mozilla-firefox-locale-en-gb.list
/var/lib/dpkg/info/mozilla-firefox-locale-en-gb.md5sums
/var/lib/mozilla-firefox/extensions.d
/var/lib/mozilla-firefox/extensions.d/50en-GB-locale.ext
dad@dad-desktop:~$ 
```

---

### Post by kpkeerthi on 2008-08-01
OK. So firefox is in /opt (you probably copied the official mozilla build here using some sort of a script). It would have been in /usr/lib if you have used a .deb file. 

Here is what you need to do:

1. Delete it
```
cd /opt
```
```
sudo rm -rf firefox
```

2. Check if firefox launches when you click on the Menu item. If it doesn't you are good.

3. Optionally, remove all personalization you have in it
```
cd ~ 
```
```
rm -rf ~/.mozilla
```
* You will loose all your bookmarks 

4. Now install it from the repository
```
sudo aptitude install firefox
```

---

### Post by mikewhatever on 2008-08-01
You mist have installed Firefox beta by unpacking the tar.gz to /opt.
Run the following commands and then post the output of <locate firefox> again:
sudo rm -r /opt/firefox   
sudo rm /usr/bin/firefox
sudo rm -r /usr/lib/firefox
sudo rm -r /usr/lib/firefox-addons

---

### Post by staib on 2008-08-01
> **mikewhatever said:**
> You mist have installed Firefox beta by unpacking the tar.gz to /opt.
Run the following commands and then post the output of <locate firefox> again:
rm -r .mozilla           #this will remove your bookmarks
sudo rm -r /opt/firefox   
sudo rm /usr/bin/firefox
sudo rm -r /usr/lib/firefox
sudo rm -r /usr/lib/firefox-addons

OK let's start explaining...

First of all I did as suggested by kpkeerthi.  Everything seemed to be good and I installed 3.0 from the repository - BUT although new menu entries appeared for firefox it would not run...

When I clicked on the Firefox entry in the menu I get "Failed to execute child process "firefox" (No such file or directory)"

So I removed FF 3.0 again and went through the similar but slightly different commands above - and, as you suggested, then ran <locate firefox> again - this is the current output (I have snipped a large number of 'cache' lines to clean it up):


```
/home/andrea/.mozilla/firefox/5e2aem9v.default/Cache/C345FE0Fd01
<snip>
/.mozilla/firefox/5e2aem9v.default/Cache/_CACHE_001_
/home/andrea/.mozilla/firefox/5e2aem9v.default/Cache/_CACHE_002_
/home/andrea/.mozilla/firefox/5e2aem9v.default/Cache/_CACHE_003_
/home/andrea/.mozilla/firefox/5e2aem9v.default/Cache/_CACHE_MAP_
/home/andrea/.mozilla/firefox/5e2aem9v.default/OfflineCache/index.sqlite
/home/andrea/.mozilla/firefox/5e2aem9v.default/bookmarkbackups/bookmarks-2008-07-14.html
/home/andrea/.mozilla/firefox/5e2aem9v.default/bookmarkbackups/bookmarks-2008-07-29.html
/home/andrea/.mozilla/firefox/5e2aem9v.default/bookmarkbackups/bookmarks-2008-07-30.html
/home/andrea/.mozilla/firefox/5e2aem9v.default/bookmarkbackups/bookmarks-2008-07-31.html
/home/andrea/.mozilla/firefox/5e2aem9v.default/bookmarkbackups/bookmarks-2008-08-01.html
/home/andrea/.mozilla/firefox/5e2aem9v.default/chrome/userChrome-example.css
/home/andrea/.mozilla/firefox/5e2aem9v.default/chrome/userContent-example.css
/home/andrea/.mozilla/firefox/Crash Reports/InstallTime2008020513
/home/andrea/.mozilla/firefox/Crash Reports/LastCrash
/home/andrea/.mozilla/firefox/Crash Reports/UserID
/home/andrea/.mozilla/firefox/Crash Reports/crashreporter.ini
/home/andrea/.mozilla/firefox/Crash Reports/pending
/home/andrea/.mozilla/firefox/Crash Reports/submit.log
/home/dad/.gnome2/panel2.d/default/launchers/firefox-1.desktop
/home/dad/.icons/firefox-document.png
/home/dad/.local/share/applications/firefox.desktop
/home/kyle/.icons/firefox-document.png
/home/kyle/.mozilla/firefox
/home/kyle/.mozilla/firefox/89ytrjzj.default
/home/kyle/.mozilla/firefox/Crash Reports
/home/kyle/.mozilla/firefox/pluginreg.dat
/home/kyle/.mozilla/firefox/profiles.ini
/home/kyle/.mozilla/firefox/89ytrjzj.default/.parentlock
/home/kyle/.mozilla/firefox/89ytrjzj.default/Cache
/home/kyle/.mozilla/firefox/89ytrjzj.default/OfflineCache
/home/kyle/.mozilla/firefox/89ytrjzj.default/XPC.mfasl
/home/kyle/.mozilla/firefox/89ytrjzj.default/XUL.mfasl
/home/kyle/.mozilla/firefox/89ytrjzj.default/blocklist.xml
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarkbackups
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarks.bak
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarks.html
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarks.postplaces.html
/home/kyle/.mozilla/firefox/89ytrjzj.default/cert8.db
/home/kyle/.mozilla/firefox/89ytrjzj.default/chrome
/home/kyle/.mozilla/firefox/89ytrjzj.default/compatibility.ini
/home/kyle/.mozilla/firefox/89ytrjzj.default/compreg.dat
/home/kyle/.mozilla/firefox/89ytrjzj.default/content-prefs.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/cookies.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/downloads.rdf
/home/kyle/.mozilla/firefox/89ytrjzj.default/downloads.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/extensions
/home/kyle/.mozilla/firefox/89ytrjzj.default/extensions.cache
/home/kyle/.mozilla/firefox/89ytrjzj.default/extensions.ini
/home/kyle/.mozilla/firefox/89ytrjzj.default/extensions.rdf
/home/kyle/.mozilla/firefox/89ytrjzj.default/formhistory.dat
/home/kyle/.mozilla/firefox/89ytrjzj.default/formhistory.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/history.dat
/home/kyle/.mozilla/firefox/89ytrjzj.default/key3.db
/home/kyle/.mozilla/firefox/89ytrjzj.default/localstore.rdf
/home/kyle/.mozilla/firefox/89ytrjzj.default/mimeTypes.rdf
/home/kyle/.mozilla/firefox/89ytrjzj.default/minidumps
/home/kyle/.mozilla/firefox/89ytrjzj.default/permissions.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/places.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/pluginreg.dat
/home/kyle/.mozilla/firefox/89ytrjzj.default/prefs.js
/home/kyle/.mozilla/firefox/89ytrjzj.default/search.rdf
/home/kyle/.mozilla/firefox/89ytrjzj.default/search.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/secmod.db
/home/kyle/.mozilla/firefox/89ytrjzj.default/signons3.txt
/home/kyle/.mozilla/firefox/89ytrjzj.default/urlclassifier2.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/urlclassifier3.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/xpti.dat
/home/kyle/.mozilla/firefox/89ytrjzj.default/Cache/031B6E13d01
<snip>
/home/kyle/.mozilla/firefox/89ytrjzj.default/Cache/_CACHE_001_
/home/kyle/.mozilla/firefox/89ytrjzj.default/Cache/_CACHE_002_
/home/kyle/.mozilla/firefox/89ytrjzj.default/Cache/_CACHE_003_
/home/kyle/.mozilla/firefox/89ytrjzj.default/Cache/_CACHE_MAP_
/home/kyle/.mozilla/firefox/89ytrjzj.default/OfflineCache/index.sqlite
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarkbackups/bookmarks-2008-07-12.html
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarkbackups/bookmarks-2008-07-13.html
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarkbackups/bookmarks-2008-07-27.html
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarkbackups/bookmarks-2008-07-28.html
/home/kyle/.mozilla/firefox/89ytrjzj.default/bookmarkbackups/bookmarks-2008-07-31.html
/home/kyle/.mozilla/firefox/89ytrjzj.default/chrome/userChrome-example.css
/home/kyle/.mozilla/firefox/89ytrjzj.default/chrome/userContent-example.css
/home/kyle/.mozilla/firefox/89ytrjzj.default/minidumps/277dee33-833a-71df-219ac395-0bb35596.dmp
/home/kyle/.mozilla/firefox/89ytrjzj.default/minidumps/277dee33-833a-71df-219ac395-0bb35596.extra
/home/kyle/.mozilla/firefox/89ytrjzj.default/minidumps/4eb8ee3e-ed4e-152a-2edd5432-68a6f92a.dmp
/home/kyle/.mozilla/firefox/Crash Reports/InstallTime2008020513
/home/kyle/.mozilla/firefox/Crash Reports/LastCrash
/home/kyle/.mozilla/firefox/Crash Reports/UserID
/home/kyle/.mozilla/firefox/Crash Reports/crashreporter.ini
/home/kyle/.mozilla/firefox/Crash Reports/pending
/home/kyle/.mozilla/firefox/Crash Reports/submit.log
/usr/bin/firefox
/usr/bin/firefox-3.0
/usr/bin/firefox.ubuntu
/usr/bin/mozilla-firefox
/usr/lib/firefox
/usr/lib/firefox-3.0.1
/usr/lib/firefox-addons
/usr/lib/firefox-3.0.1/.autoreg
/usr/lib/firefox-3.0.1/application.ini
/usr/lib/firefox-3.0.1/blocklist.xml
/usr/lib/firefox-3.0.1/browserconfig.properties
/usr/lib/firefox-3.0.1/chrome
/usr/lib/firefox-3.0.1/components
/usr/lib/firefox-3.0.1/defaults
/usr/lib/firefox-3.0.1/dictionaries
/usr/lib/firefox-3.0.1/extensions
/usr/lib/firefox-3.0.1/ffox-3-beta-profile-migration-dialog
/usr/lib/firefox-3.0.1/firefox
/usr/lib/firefox-3.0.1/firefox-3.0-restart-required.update-notifier
/usr/lib/firefox-3.0.1/firefox.sh
/usr/lib/firefox-3.0.1/icons
/usr/lib/firefox-3.0.1/modules
/usr/lib/firefox-3.0.1/plugins
/usr/lib/firefox-3.0.1/run-mozilla.sh
/usr/lib/firefox-3.0.1/searchplugins
/usr/lib/firefox-3.0.1/chrome/browser.jar
/usr/lib/firefox-3.0.1/chrome/browser.manifest
/usr/lib/firefox-3.0.1/chrome/classic.jar
/usr/lib/firefox-3.0.1/chrome/classic.manifest
/usr/lib/firefox-3.0.1/chrome/en-US.jar
/usr/lib/firefox-3.0.1/chrome/en-US.manifest
/usr/lib/firefox-3.0.1/chrome/icons
/usr/lib/firefox-3.0.1/chrome/icons/default
/usr/lib/firefox-3.0.1/chrome/icons/default/default16.png
/usr/lib/firefox-3.0.1/chrome/icons/default/default32.png
/usr/lib/firefox-3.0.1/chrome/icons/default/default48.png
/usr/lib/firefox-3.0.1/components/FeedConverter.js
/usr/lib/firefox-3.0.1/components/FeedWriter.js
/usr/lib/firefox-3.0.1/components/WebContentConverter.js
/usr/lib/firefox-3.0.1/components/aboutRobots.js
/usr/lib/firefox-3.0.1/components/browser.xpt
/usr/lib/firefox-3.0.1/components/fuelApplication.js
/usr/lib/firefox-3.0.1/components/libbrowsercomps.so
/usr/lib/firefox-3.0.1/components/libbrowserdirprovider.so
/usr/lib/firefox-3.0.1/components/nsBrowserContentHandler.js
/usr/lib/firefox-3.0.1/components/nsBrowserGlue.js
/usr/lib/firefox-3.0.1/components/nsMicrosummaryService.js
/usr/lib/firefox-3.0.1/components/nsPlacesTransactionsService.js
/usr/lib/firefox-3.0.1/components/nsSafebrowsingApplication.js
/usr/lib/firefox-3.0.1/components/nsSearchService.js
/usr/lib/firefox-3.0.1/components/nsSearchSuggestions.js
/usr/lib/firefox-3.0.1/components/nsSessionStartup.js
/usr/lib/firefox-3.0.1/components/nsSessionStore.js
/usr/lib/firefox-3.0.1/components/nsSetDefaultBrowser.js
/usr/lib/firefox-3.0.1/components/nsSidebar.js
/usr/lib/firefox-3.0.1/defaults/preferences
/usr/lib/firefox-3.0.1/defaults/profile
/usr/lib/firefox-3.0.1/defaults/syspref
/usr/lib/firefox-3.0.1/defaults/preferences/channel-prefs.js
/usr/lib/firefox-3.0.1/defaults/preferences/firefox-branding.js
/usr/lib/firefox-3.0.1/defaults/preferences/firefox-l10n.js
/usr/lib/firefox-3.0.1/defaults/preferences/firefox.js
/usr/lib/firefox-3.0.1/defaults/preferences/ubuntu-useragent.js
/usr/lib/firefox-3.0.1/icons/document.png
/usr/lib/firefox-3.0.1/icons/mozicon128.png
/usr/lib/firefox-3.0.1/icons/mozicon16.xpm
/usr/lib/firefox-3.0.1/icons/mozicon50.xpm
/usr/lib/firefox-3.0.1/modules/distribution.js
/usr/share/firefox
/usr/share/app-install/desktop/firefox-2.desktop
/usr/share/app-install/desktop/firefox-greasemonkey.desktop
/usr/share/app-install/desktop/firefox-launchpad-plugin.desktop
/usr/share/app-install/desktop/firefox-sage.desktop
/usr/share/app-install/desktop/firefox-showcase.desktop
/usr/share/app-install/desktop/firefox-themes-ubuntu.desktop
/usr/share/app-install/desktop/firefox-ubuntu-it-menu.desktop
/usr/share/app-install/desktop/firefox-webdeveloper.desktop
/usr/share/app-install/desktop/firefox.desktop
/usr/share/app-install/icons/firefox-greasemonkey.xpm
/usr/share/app-install/icons/firefox-launchpad-plugin.xpm
/usr/share/app-install/icons/firefox-sage.xpm
/usr/share/app-install/icons/firefox-showcase.xpm
/usr/share/app-install/icons/firefox-themes-ubuntu.xpm
/usr/share/app-install/icons/firefox-ubuntu-it-menu.png
/usr/share/app-install/icons/firefox-webdeveloper.xpm
/usr/share/applications/firefox.desktop
/usr/share/apport/package-hooks/firefox-3.0.py
/usr/share/apport/package-hooks/firefox.pyc
/usr/share/bug/firefox-3.0
/usr/share/bug/firefox-3.0/presubj
/usr/share/doc/firefox-3.0
/usr/share/doc/mozilla-firefox-locale-en-gb
/usr/share/doc/firefox-3.0/MPL.gz
/usr/share/doc/firefox-3.0/changelog.Debian.gz
/usr/share/doc/firefox-3.0/copyright
/usr/share/doc/firefox-3.0/firefox.cfg
/usr/share/doc/mozilla-firefox-locale-en-gb/changelog.Debian.gz
/usr/share/doc/mozilla-firefox-locale-en-gb/copyright
/usr/share/firefox/defaults
/usr/share/firefox/defaults/pref
/usr/share/firefox/defaults/pref/apturl.js
/usr/share/menu/firefox-3.0
/usr/share/pixmaps/firefox-3.0.png
/var/cache/apt/archives/firefox-3.0-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_i386.deb
/var/cache/apt/archives/firefox-3.0-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb
/var/cache/apt/archives/firefox-3.0_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_i386.deb
/var/cache/apt/archives/firefox-3.0_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb
/var/cache/apt/archives/firefox-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_all.deb
/var/cache/apt/archives/firefox-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_all.deb
/var/cache/apt/archives/firefox_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_all.deb
/var/cache/apt/archives/firefox_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_all.deb
/var/lib/mozilla-firefox
/var/lib/dpkg/alternatives/firefox-flashplugin
/var/lib/dpkg/info/firefox-3.0.conffiles
/var/lib/dpkg/info/firefox-3.0.list
/var/lib/dpkg/info/firefox-3.0.md5sums
/var/lib/dpkg/info/firefox-3.0.postinst
/var/lib/dpkg/info/firefox-3.0.postrm
/var/lib/dpkg/info/firefox-3.0.prerm
/var/lib/dpkg/info/mozilla-firefox-locale-en-gb.list
/var/lib/dpkg/info/mozilla-firefox-locale-en-gb.md5sums
/var/lib/mozilla-firefox/extensions.d
/var/lib/mozilla-firefox/extensions.d/50en-GB-locale.ext
dad@dad-desktop:~$ 
```

---

### Post by mikewhatever on 2008-08-01
Well, the executable /usr/bin/firefox is still in place and we don't know whether it's the current version or the beta one. Are you sure you've run the third command? It explicitly removes the said file.
I'd open Synaptic and mark firefox for 'Complete Removal' if possible. Try looking for variations, such as firefox-3 or firefox-2 and make sure none installed. Then run the commands again and try reinstalling the current version of firefox.

I've removed the first command since we don't really care about ./mozilla directory.

---

### Post by staib on 2008-08-01
> **mikewhatever said:**
> Well, the executable /usr/bin/firefox is still in place and we don't know whether it's the current version or the beta one. Are you sure you've run the third command? It explicitly removes the said file.
I'd open Synaptic and mark firefox for 'Complete Removal' if possible. Try looking for variations, such as firefox-3 or firefox-2 and make sure none installed. Then run the commands again and try reinstalling the current version of firefox.

I've removed the first command since we don't really care about ./mozilla directory.

Thanks for the continued advice - much appreciated. 

I ran Synaptic and you were right - there was a firefox still lurking there - it's now been removed with synaptic.

However when I then run <locate firefox> it still returns an entry of

```
/usr/bin/firefox
/usr/bin/firefox-3.0
/usr/bin/firefox.ubuntu
/usr/bin/mozilla-firefox
/usr/lib/firefox
/usr/lib/firefox-3.0.1
/usr/lib/firefox-addons

``` 

I will try doing your commands again and checking this again...

---

### Post by staib on 2008-08-01
> **staib said:**
> I will try doing your commands again and checking this again...

These were the commands and results:

```
dad@dad-desktop:~$ sudo rm -r /opt/firefox
rm: cannot remove `/opt/firefox': No such file or directory
dad@dad-desktop:~$ sudo rm /usr/bin/firefox
rm: cannot remove `/usr/bin/firefox': No such file or directory
dad@dad-desktop:~$ sudo rm -r /usr/lib/firefox
rm: cannot remove `/usr/lib/firefox': No such file or directory
dad@dad-desktop:~$ sudo rm -r /usr/lib/firefox-addons
rm: cannot remove `/usr/lib/firefox-addons': No such file or directory
```

Which suggests that all were completed first time...

If I look in usr/bin I can't see any reference to firefox...

But <locate firefox> still shows the entry...

Just tried reinstalling FF3.0 (via Synaptic) but no joy - I'm sure it has installed but I dont know how to get it to run.

---

### Post by staib on 2008-08-01
OK - finally cracked it.  I tried the command 'firefox 3.0' and then noticed that the error message suggested downloading 'firefox-3.0'

So I tried the command 'firefox-3.0' and all was then good.

Thanks all for your patient help this afternoon - so kind of you all.

Nick

---

### Post by nxt on 2008-09-05
I have purged the old FF and got the new firefox 3.0.1 running. Hoverever I am not able to access internet - it just keeps loading without an end. Konqueror and everything else seems to work fine. I am not in Offline mode and I also tried to fiddle with the ipv6 settings with no result :(

any help would be appreciated...

---

### Post by kpkeerthi on 2008-09-08
> **nxt said:**
> I have purged the old FF and got the new firefox 3.0.1 running. Hoverever I am not able to access internet - it just keeps loading without an end. Konqueror and everything else seems to work fine. I am not in Offline mode and I also tried to fiddle with the ipv6 settings with no result :(

any help would be appreciated...

Clear your profile folder ~/.mozilla under your home and try again.
```
rm -rf ~/.mozilla
```

**Note: **You will loose your book marks and add-ons. So back up if required.

---

### Post by stalkingwolf on 2008-09-08
To save your bookmarks open firefox. click Bookmarks, then
Manage Bookmarks,this may also be called organize bookmarks
 then export.  This will export and save them
to any place you want.

Then when you get firefox back and running repeat the process
selecting Import - from file , follow the instructions and
it will import your Bookmarks back in.

---

