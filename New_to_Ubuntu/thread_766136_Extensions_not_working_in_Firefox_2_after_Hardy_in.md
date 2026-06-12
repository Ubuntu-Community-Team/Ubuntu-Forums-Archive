---
title: "Extensions not working in Firefox 2 after Hardy install"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by aerojad on 2008-04-25
The extensions I want aren't in the Firefox 3 beta yet, so I went ahead and removed firefox 3 and installed the firefox-2 package.  Now every time I download an extension I get this error when I try to install:

Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 7647

What do I do?

---

### Post by aerojad on 2008-04-25
any ideas?  I probably would have sat on Gusty if I knew I had to go with the Firefox 3 beta.  Nothing I'm used to working is working and it is making the whole expierence rather annoying.

---

### Post by Bubba64 on 2008-04-25
If you did a straight upgrade and your extensions which I think your talking about the add ons are not working, if you install nightly tester tools from add ons in FF 3 it will get the add ons working.

---

### Post by Saya on 2008-04-25
You can install Firefox 2 in Hardy with sudo apt-get install firefox-2.

---

### Post by vegitaj on 2008-04-25
hi, i was able to use both ff2 and ff3 after upgrading to hardy ... tho it took me forever to figure out how ... i needed to use Zotero for research, an extension not supported by ff3 yet.

according synaptic package manager the 'firefox-2' and 'firefox' (ff 3) packages were installed after i upgraded to hardy.  

so, i created a new profile to use for ff 2 using profile manager.  in terminal : ```
firefox-2 --profilemanager
``` (and called the profile 'researchfox')

then i added a 'custom application launcher' to the panel, with this as the 'command' ```
firefox-2 -P researchfox
``` and then changed the existing firefox launcher properties in the panel to the command: ```
firefox -P default  
``` (where 'default' is your original profile name)

now i can use Zotero again and keep ff3 for streaming video and other stuff improvements (like smart bookmarks).  

i suppose you could also switch back to ff2 by just changing the launcher from 'firefox' to 'firefox-2'.

---

