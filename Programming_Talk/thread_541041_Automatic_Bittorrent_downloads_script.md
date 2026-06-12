---
title: "Automatic Bittorrent downloads script"
date: 2007-09-02
forum: Programming Talk
---

### Post by Erucolindo on 2007-09-02
Hi!

I've got a server in the closet running Ubuntu 6.06 witch I use as a fileserver throught ssh (MacFusion and sshfs on the clientside). When I download stuff nowadays I download them on my mac and then copy the files to the server.

Then I thoght it would be easier downloading them on the server directly. 

The way I like this to work is that I download the .torrent file on my mac and then put it on the server in the apropriet folder. A script then traverses the folderstructure and adds all the .torrent files and downloads them and then puts them back in the correct folder. The torrent then stops sharing after a certtent ratio.

Any thoughts how to pull this off? I am looking at bittorrent-console and pytorrent to do the transfers. I'm uncertain how to handel the files.

Any help or ideas appreitiated! Sorry for my english...

---

### Post by SOULRiDER on 2007-09-02
How about using that BT client with a web interface (torrent flux)?

[http://ubuntuforums.org/showthread.php?t=268985&highlight=torrent](http://ubuntuforums.org/showthread.php?t=268985&highlight=torrent)

---

### Post by Erucolindo on 2007-09-02
I'm testing that as I type.. I agree it has lots more power, and so far the setup seems to work.

Thanks!

---

### Post by nanotube on 2007-09-05
you could also use a console-based torrent client, like rtorrent.
just ssh to your server, and fire up rtorrent to pull down your torrents.

---

### Post by Erucolindo on 2007-09-05
Well, sure I can do that, but I think it would be to much of a hassle, first scp the torrent file over there, then fire up screen, then start the torrentprogram (rtorrent, mainline, transmissioncli etc.), then login out..

I like the commandline, just not that much. ;)

I would have to run a cli client that could be configured just by flags, then I would hav a script invoking that program when it sees a .torrent file in the directory structure.

I liked the torrentflux idea, but it was a bit to heavy for my use.

I need some input how to traverse (looking throught) a directory structure, and what a good cli torrent program would be.

I use Transmission on my Mac and thinks it performs fairly well. Anyone tested the linux cli version (trasmissioncli). Or perhaps something better? Can you run BitTyrant in cli?

---

### Post by nanotube on 2007-09-05
> **Erucolindo said:**
> Well, sure I can do that, but I think it would be to much of a hassle, first scp the torrent file over there, then fire up screen, then start the torrentprogram (rtorrent, mainline, transmissioncli etc.), then login out..

I like the commandline, just not that much. ;)

I would have to run a cli client that could be configured just by flags, then I would hav a script invoking that program when it sees a .torrent file in the directory structure.

I liked the torrentflux idea, but it was a bit to heavy for my use.

I need some input how to traverse (looking throught) a directory structure, and what a good cli torrent program would be.

I use Transmission on my Mac and thinks it performs fairly well. Anyone tested the linux cli version (trasmissioncli). Or perhaps something better? Can you run BitTyrant in cli?

well, you can traverse a directory structure with just about anything - bash, python, perl... :)

---

### Post by Erucolindo on 2007-09-06
Sure, but the only language I know how to do it in is LISP and that is not realy applicable. The code would look somthing like this:

```
if "the first file" = *.torrent then torrentapp add xyz.torrent and test "the rest of the files"
elseif "the first file" = directory then test directory and test "the rest of the files"
else test "the rest of the files"
```

Now you se how damaged I am by LISP. Can you even do functional programing in bash? Or how would you do it?

---

### Post by Erucolindo on 2007-09-07
Hade some time to do some more research, and this is what i got so far:

```
#!/bin/bash

traverse() 
{
  # Traverse a directory

  ls "$1" | while read i
  do
    if [ -d "$1/$i" ]
    then
      traverse "$1/$i"
    else 
      if [[ "$i" =~ "*.torrent" ]]
      then torrent "$1/$i"
      fi
    fi
  done
}

traverse /ftp
```

now i need a torrent program (replacing "torrent" in the code) suitible for the task.. 
what do you think?

---

### Post by Erucolindo on 2007-09-07
Soo, I couldn't put the matter to rest. Did some more research and many people suggest rtorrent so I decided to use it. Here's the latest code:

```
#!/bin/bash

traverse() 
{
  # Traverse a directory

  ls "$1" | while read i
  do
    if [ -d "$1/$i" ]
    then
      traverse "$1/$i"
    else 
      if [[ "$i" =~ "*.torrent" ]]
      then 
      	do 
      		rtorrent -d "$1" "$1/$i"
      		rm "$1/$i"
      	done
      fi
    fi
  done
}

traverse /ftp/Download
```

I haven't tested it yet. Maybe this weekend I will give it a spinn and see if it's any good.

---

### Post by bobbocanfly on 2007-09-07
Could you not just stick Samba on the server and download everything to a Samba share? Currently what i do, works perfectly.

---

### Post by Erucolindo on 2007-09-08
> Could you not just stick Samba on the server and download everything to a Samba share? Currently what i do, works perfectly.

No. I do not want to use samba since sshfs does the same thing better then a samba setup does. And the point of the exercise is that my server is sopposed to download my torrents, since my macbook is not always on the network.

---

