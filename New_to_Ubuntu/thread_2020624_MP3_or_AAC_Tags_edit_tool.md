---
title: "MP3 or AAC Tags edit tool"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-08
For Ubuntu ... is there any software, which used to edit **MP3** or **AAC** Tags?
What it names?

**PS:**
A software, which capable to displayed **all iTunes' Tags** preferred.
Thank you.

---

### Post by irv on 2012-07-08
There is one call EasyTAG.
I never used it but maybe you can check it out. it is in the Software Center.
[ATTACH]220905[/ATTACH]

---

### Post by papibe on 2012-07-08
I czgirb.

There are several [ID3 tags]("http://en.wikipedia.org/wiki/Id3_tag") editors on the Software Center including EasyTAG, and Kid3-qt.

Hope that helps.
Regards.

---

### Post by Shadius on 2012-07-08
I use EasyTag, it's not bad.

---

### Post by Cheesemill on 2012-07-08
I was never very impressed by any of the applications available in the Software Center, but I recently discovered Puddletag.

[http://www.webupd8.org/2011/01/puddletag-awesome-mp3tag-like-editor.html](http://www.webupd8.org/2011/01/puddletag-awesome-mp3tag-like-editor.html)

---

### Post by Shadius on 2012-07-08
> **Cheesemill said:**
> I was never very impressed by any of the applications available in the Software Center, but I recently discovered Puddletag.

[http://www.webupd8.org/2011/01/puddletag-awesome-mp3tag-like-editor.html](http://www.webupd8.org/2011/01/puddletag-awesome-mp3tag-like-editor.html)

This looks much better than EasyTAG. Will try it out!

---

### Post by spcwingo on 2012-07-08
I use TagTool.  It's very simple and gets the job done.  It's in the repos (universe repo to be exact).

---

### Post by czgirb on 2012-07-09
> **spcwingo said:**
> I use TagTool.  It's very simple and gets the job done.  It's in the repos (universe repo to be exact).

I just found MP3Diags, it looks nice ... but I don't know how to install it.
Have a clue?

PS:
Puddletag looks nice, but I need the Composer tags. Cos iTunes got one.
And this part is the part I require in editing process.

---

### Post by irv on 2012-07-09
The easy way is to go to a terminal and type:
```
sudo apt-get install mp3diags
```
or just go to the Software center and install from there.
[ATTACH]220958[/ATTACH]

---

### Post by czgirb on 2012-07-09
> **irv said:**
> The easy way is to go to a terminal and type:
```
sudo apt-get install mp3diags
```or just go to the Software center and install from there.
[ATTACH]220958[/ATTACH]

Thank you.

---

### Post by irv on 2012-07-09
> **czgirb said:**
> Thank you.

Your Welcome

---

### Post by Cheesemill on 2012-07-09
> **czgirb said:**
> PS:
Puddletag looks nice, but I need the Composer tags.

You can edit the composer tags with Puddletag.

---

### Post by czgirb on 2012-07-09
> **Cheesemill said:**
> You can edit the composer tags with Puddletag.

Oh yeah ???
SORRY !!! I said it unable to edit Composer, cos I see the Screenshot ... [http://cdn2.techie-buzz.com/images/ricky/puddletag.png](http://cdn2.techie-buzz.com/images/ricky/puddletag.png)
And I find no Composer in its detail.
Would you mind for giving me a Screenshot with Composer's column ?
Is the application can be installed through Ubuntu Software Center also ?

---

### Post by irv on 2012-07-09
> **czgirb said:**
> Oh yeah ???
SORRY !!! I said it unable to edit Composer, cos I see the Screenshot ... [http://cdn2.techie-buzz.com/images/ricky/puddletag.png](http://cdn2.techie-buzz.com/images/ricky/puddletag.png)
And I find no Composer in its detail.
Would you mind for giving me a Screenshot with Composer's column ?
Is the application can be installed through Ubuntu Software Center also ?

Yes, you can install through the Software Center or command like or the package manager. Which ever way you like. Ubuntu makes it easy to install apps.

---

### Post by czgirb on 2012-07-10
> **irv said:**
> Yes, you can install through the Software Center or command like or the package manager. Which ever way you like. Ubuntu makes it easy to install apps.
Yesterday, I installed Puddletag and make it scan my lossy file (100GB+) ... it used all my physical 2GB memory + 2GB swap. My swap at least used !

---

### Post by Cheesemill on 2012-07-10
> **czgirb said:**
> Oh yeah ???
SORRY !!! I said it unable to edit Composer, cos I see the Screenshot ... [http://cdn2.techie-buzz.com/images/ricky/puddletag.png](http://cdn2.techie-buzz.com/images/ricky/puddletag.png)
And I find no Composer in its detail.
Would you mind for giving me a Screenshot with Composer's column ?
Is the application can be installed through Ubuntu Software Center also ?

See attached screenshot.

To add the Composer column just right-click on any of the column headings and select 'Select Columns...'

Click on the + sign to add a new column and enter Composer for the name and composer for the field.

Puddletag isn't in the repositories yet, to install it just do:
```
sudo add-apt-repository ppa:webupd8team/puddletag
sudo apt-get update
sudo apt-get install puddletag
```

---

### Post by czgirb on 2012-07-10
Both **MP3Diag** and **Puddletag** are able to be installed from **Ubuntu Software Center**.
Tried both ... and now (for my taste), I prefer **Puddletag**. So, I uninstalled **MP3Diag**.

---

### Post by 3dmatrix on 2012-11-18
Easy Tag crashes in 12.04.
It worked fine in earlier versions.

---

### Post by andrew.46 on 2012-11-19
Thanks to all of the recommendations for Puddletag I have installed it: love it :). EasyTag has now gone!

---

### Post by 3dmatrix on 2012-11-19
Puddletag works fine !

---

