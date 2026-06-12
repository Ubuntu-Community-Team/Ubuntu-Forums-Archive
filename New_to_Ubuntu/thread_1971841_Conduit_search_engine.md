---
title: "Conduit search engine"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by Populus on 2012-05-02
I tried to download a file conversion programme via WiseConvert today.  It told me to install its search engine and said I could remove it once  the programme was installed. Should have suspected something - Firefox  couldn't access the web page and I now can't remove this lousy  Conduit.com search engine. It's hijacking my searches, preventing me  from finding out how to get rid of it - but I did find posts from other  victims who had a lot of trouble removing it. The problem is that they were all running Windows. Can anyone help?!

---

### Post by xedi on 2012-05-03
I don't know anything about the search engine but before somebody else more knowledgeable can reply, some general thoughts you might want to try out and might work:

How did you install the search engine? Was it an add-on for firefox, was it a .deb you installed? Does it hijack only firefox or other browsers such as chromium/chrome?

If it only affects firefox, then you could use chromium to research on how to fix this problem. I just did a quick google search and it seems that it is "only" a firefox add-on, which is hard to remove but is nevertheless a good sign.

If you don't have any important stuff from firefox to keep like bookmarks and passwords, I would just delete the firefox home folder. In your home directory, push ctrl+h to see hidden directories. There should be a .mozilla directory which should contain configuration files and other personal firefox data. Make a backup of the folder in case you want to keep some of the data. Delete the .mozilla folder and restart firefox and check out whether you got rid of it.

If not, you could try a complete removal of firefox. The fastest way to do that, would be to open the terminal (type in terminal in the dash) and to write following line 

```
sudo apt-get purge firefox
```

hit enter and type in your password.

and then reinstall it ```
sudo apt-get install firefox
```

---

### Post by strask on 2012-05-03
I don't think all that is probably needed. 

As a test, I logged in as a test user on my machine and installed the toolbar myself. I was able to remove it by going to the Tools menu -> Add-ons -> Extensions, select the evil toolbar, click remove. Restart firefox. Then all that remains is to change your homepage back to what it was before.

But if for some reason that doesn't work, purging firefox as described above should probably do the trick.

---

### Post by Populus on 2012-05-03
Thank you for your suggestions. I got Conduit by installing a .deb. Despite being told that I could remove the search engine after downloading the programme I wanted, I went to Conduit's help page and the response to the FAQ 'how do I remove Conduit search engine?' was 'the search engine cannot be modified or removed'. Clearly this was BS designed to con people into keeping the thing, but I couldn't access Tools/Add-ons - it was greyed out. I had a look this morning and found a post on another forum which said to type in about:config and check for conduit files. I did this and removed loads of files (reset) and got my Firefox page back. I've purged and reinstalled Firefox as a precaution and I've also now installed Google Chrome, which hasn't been affected. I'm still a bit wary though, as someone on the other site said he'd found lots of hidden self-replicating files and he'd had to wipe and reinstall Ubuntu to get rid of them. It seems a lot of users have had trouble with Conduit, mainly through services like uTorrent/BitTorrent. Definitely malware and one to be avoided.

---

### Post by xedi on 2012-05-03
If you installed it through a .deb then you could try purging the package(s) which it installed, too.

I can recommend synaptic for this, which you can get in the software-center. With it you can search for conduit packages and purge them graphically instead of using the terminal command and "guessing" what the package name is you want to remove.

---

### Post by Populus on 2012-05-04
How do I go about this? I'm quite new to Ubuntu and pretty lame with IT generally :rolleyes:

---

