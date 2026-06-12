---
title: "Would you put Drupal 6 or 7 on Ubuntu (6 is in the repository)"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-03-21
I just found out about [Drupal ]("http://drupal.org/")being a good program for setting up a web site.

I see "drupal6" in the Ubuntu Software Center; but I read that version 7.x is the current version ([and that each version gets easier]("http://www.google.com/url?sa=t&rct=j&q=wikipedia%20drupal&source=web&cd=1&ved=0CDEQFjAA&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FDrupal&ei=9IBqT72iF-ajiQKdus2LBQ&usg=AFQjCNFa4aWwqOfkNHfxpQZzfYLV7xW1jg&cad=rja")).

Since I've never used Drupal, and all I know is basic HTML tagging, I'd want the ease of use of the latest version (I would think); but since I've never installed Drupal, I'd want the ease of installation of the Ubuntu Software Center (I would think).

If you've used Drupal, I would love to know what your advice is.

thanks!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214736&stc=1&d=1332379835[/IMG]

---

### Post by Derek Karpinski on 2012-03-22
I've never installed drupal, so take it with a grain of salt, but.......

I did install wordpress both from Software center, and downloading it, and joomla from the web, and personally, I think downloading it, and installing it manually is easier.

But, you need to install some pre-requisite packages before you download and try to run the setup.

```
sudo apt-get update && sudo apt-get install lamp-server^
```

NO, the '^' (caret) is not a mistake.

Don't forget to create a 'root' password for mysql......remember it.

At that point, you probably will be able to download drupal and set it up manually.

If that sounds like too much, install it from the software center.

The main thing I didn't like about installing from the software center was it didn't put wordpress in the /var/www folder.  I had to symlink it there.

I suggest creating a virtual machine with Ubuntu Server edition, and virtualbox, take a snapshot after the clean install, and installing it there.  I royally screwed up my installation.

---

### Post by cressrt on 2012-03-22
I prefer Joomla, download from the web, or with a lot of hosting companies you can install direct to your site rather than having to upload.

---

