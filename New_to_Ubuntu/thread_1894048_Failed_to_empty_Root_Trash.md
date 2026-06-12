---
title: "Failed to empty Root Trash"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-12-11
I recently noticed my Bootchart log folder was up to 1.2G, so tried to remove all but the latest records.
To do this by GUI, I had to open a Root Nautilus screen & navigate to /var/log/bootchart.
There, I found several thousand items, selected all but the most recent, and deleted them.
So far - so good.

But that did not free up any space, as all items ended up in Root Trash at root/.local/share/trash.
Actually twice - once in trash/files & once in trash/info.

I imagined I just had to select & delete all those items.
I tried the odd one & that seemed to work (maybe) but then I tried selecting all (Ctrl+A) & deleting, when odd things began to happen.
It seems that the content of those folders is increasing, rather than decreasing, when I delete!

I saw somewhere that I should, in Nautilus, use Go > Trash > Empty Trash, but Go > Trash leads to an error message ```
The folder contents could not be displayed.
Sorry, could not display all the contents of "trash": Operation not supported
```
So maybe I broke something?

Can anybody explain to me how to empty Root Trash?

Thanks!

---

### Post by ExileAmongYou on 2011-12-11
You will probably have to use the terminal to get this done. Be careful though, as rm can be a bit dangerous. 
First become root:
```
sudo su
```
Then I would suggest cd-ing into the /root/.local/share folder like this:
```
cd /root/.local/share
```
Then the potentially risky part:
```
rm -i -r trash/
```
While you're typing trash/, I would suggest hitting Tab. If you're in the right place, it should autocomplete.

---

### Post by bluexrider on 2011-12-11
here is a nice little tutorial I recommend
[COLOR=MAROON][B][SIZE=4][I]Trash Problems and Solutions*

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
[/I][/SIZE][/B][/COLOR]

---

### Post by 2CV67 on 2011-12-12
Thanks for both replies & thanks for the warnings!

I prefer GUI methods where possible & found the [Trash Tutorial]("http://ubuntuforums.org/showthread.php?t=898573") very clear & helpful.

The key item was that to delete something without it reappearing in the Trash can, I needed Shift+Del, not just Del.
Funny I never noticed that in many years Ubuntu-ing.
Works perfectly.
Also, the tutorial confirmed I could safely delete the trash/files folder & trash/info folder completely, without needing to select & delete their content.
They should be automatically regenerated whenever necessary.
Hope that's right too!

Again - many thanks!

---

### Post by 2CV67 on 2011-12-12
Having fixed my urgent problems (thanks!) I am now wondering about underlying questions:

1. I currently use Autotrash to keep my main Trash under control (throw away after 30 days). Should I be able to use it to control Root Trash & other users' Trash too?  How would I do that?

2. Is there really no GUI method for regulating Trash disposal, to throw out everything older than x days or to keep the Trash less than x MB? Even MS has been able to do this for years, haven't they...

Thanks for any suggestions!

---

### Post by bluexrider on 2011-12-12
> **2CV67 said:**
> Having fixed my urgent problems (thanks!) I am now wondering about underlying questions:

1. I currently use Autotrash to keep my main Trash under control (throw away after 30 days). Should I be able to use it to control Root Trash & other users' Trash too?  How would I do that?

2. Is there really no GUI method for regulating Trash disposal, to throw out everything older than x days or to keep the Trash less than x MB? Even MS has been able to do this for years, haven't they...

Thanks for any suggestions!


You might use script and trigger it from thunderbird or something
[http://ubuntuforums.org/attachment.php?attachmentid=83395&d=1220117126](http://ubuntuforums.org/attachment.php?attachmentid=83395&d=1220117126)


Please mark this thread 
(SOLVED)

---

### Post by 2CV67 on 2011-12-12
> **bluexrider said:**
> Please mark this thread(SOLVED)

I did mark it [SOLVED] when I posted last time & it says SOLVED for me...

---

