---
title: "Convert Rhythmbox &lt;-&gt; Exaile playlists"
date: 2011-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by fdm on 2011-04-27
These are some python scripts to quickly convert playlists between Rhythmbox and Exaile. This was the best way I could come up with to transfer large playlists, and it turned out to work very well for me so I thought I'd share.


Rhythmbox's playlists.xml is here:
/home/{USER}/.local/share/rhythmbox

Exaile's playlists folder is here:
/home/{USER}/.local/share/exaile


**Converting from Exaile to Rhythmbox**

exaile2rhythmbox.py
[http://pastebin.com/qiLW2zuS](http://pastebin.com/qiLW2zuS)

Paste the code from the codebox into a file named exaile2rhythmbox.py.
Copy Exaile's playlists folder into the same directory as the script.
Execute from the terminal with "python exaile2rhythmbox.py"
Your playlists.xml will be generated in the same directory as the script.


**Converting from Rhythmbox to Exaile**

rhythmbox2exaile.py
[http://pastebin.com/eGSvghnh](http://pastebin.com/eGSvghnh)

Paste the code from the codebox into a file named rhythmbox2exaile.py.
Copy Rhythmbox's playlists.xml into the same directory as the script.
Execute from the terminal with "python exaile2rhythmbox.py"
Your playlists folder will be generated in the same directory as the script.


Notes:
rhythmbox2exaile.py skips empty playlists.

---

