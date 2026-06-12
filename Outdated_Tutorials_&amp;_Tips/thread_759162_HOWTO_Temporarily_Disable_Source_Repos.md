---
title: "HOWTO: Temporarily Disable Source Repos"
date: 2008-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Iandefor on 2008-04-18
Occasionally, the source repositories (deb-src entries in /etc/apt/sources.list) might prove themselves annoying to you and you'll want to disable them.

I know I usually use whatever the development branch of Ubuntu is and occasionally want to minimize the amount of repository information I have to download (since I do it fairly frequently). If you don't need them, disabling the source repositories can reduce the amount of repository information you have to download at a time.

You won't save much in terms of download speed (I saved about 1.4 MiB's and 33 and a half seconds updating the apt cache) but if you're impatient like me it can help somewhat.

So, I threw together a couple of sed commands to "toggle" the source repositories in a .list file.

Sure, you can also open up the Software Sources dialog and do the same thing in the GUI, but doing it through the command-line is, as usual, faster.

Before you run either one, though, I recommend always making a backup of your sources.list file:
```
sudo cp -v /etc/apt/sources.list /etc/apt/sources.list.backup
```You should also run each command without the -i flag before running it for real, because the -i flag causes sed to write the changes directly to the input file. You want to review the changes sed will make to your sources.list, right?

The command to comment out the source repositories in /etc/apt/sources.list is:
```
sudo sed -i 's/^deb\-src/\#deb\-src/' /etc/apt/sources.list
```To uncomment any deb-src lines in sources.list, do the same but backwards:
```
sudo sed -i 's/^\#deb\-src/deb\-src/' /etc/apt/sources.list
```

---

