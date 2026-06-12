---
title: "HowTo: Install Plugins For Twiki 4.1 under Ubuntu 8.04"
date: 2008-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by usprinter on 2008-04-14
Twiki is an interesting and very useful tool but unfortunately, it is not convenient to install its plugins under Ubuntu. Twiki itself provides an automate tool to install plugins, but it is kind of broken.

To install a plugin, for example, the EmbedFlashPlugin, steps are:
1. visit /cgi-bin/twiki/configure 
2. click plugins
3. click "find more extensions"
4. find the EmbedFlashPlugin
5. click install
6. if you have any errors saying files cannot be created, changing folder permissions accordingly (change owner from root to www-data, for example)
7 cp the  EmbedFlashPlugin_installer to /var/lib/twiki (it is initially copied to some folder under /usr/lib/cgi-bin/)
8 run the above installer. If it reports file extender.pl is missing, follow screen instructions to download the file and save it under /var/lib/twiki/tools
9. edit /var/lib/twiki/bin/LocalLib.cfg, adding:
@localPerlLibPath = ( '/usr/lib/cgi-bin/lib' );
10. goto visit /cgi-bin/twiki/configure and enable EmbedFlashPlugIn

---

