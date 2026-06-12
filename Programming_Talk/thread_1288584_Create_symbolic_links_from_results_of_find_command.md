---
title: "Create symbolic links from results of find command"
date: 2009-10-11
forum: Programming Talk
---

### Post by osx on 2009-10-11
I'm trying to search a shared drive for .ogg and .mp3 files (podcasts) and create symbolic links to the files found.

I am using the find command to search and want to pass the results to ln to create the symbolic links.

As long as there are no spaces in the path, everything seems to work, but fails as soon as a space is encountered.

I assume this is due to the way find passes spaces in the path to the ln command. I have been trying to figure out how to use xargs to help, but I am very unfamiliar with xarg and my searching on Google and trying found suggestions has not worked.

Here is what I have so far that works as long as a space in the path is not encountered:

```
ln -s -v -t /home/john/Desktop/Podcasts `find /media/shared \( -iname "*.mp3" -o -iname "*.ogg" \)`
```

Thanks for any help.

---

### Post by unutbu on 2009-10-11
Perhaps try:
```
find /media/shared \( -iname "*.mp3" -o -iname "*.ogg" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" /home/john/Desktop/Podcasts/"$filename"' {} \;

```
The above command finds all the mp3 and ogg files in /media/shared and runs the command
```

sh -c 'filename="${0##*/}"; ln -sf "$0" /home/john/Desktop/Podcasts/"$filename"'  {}
```

on each file, substituting the long path name for {}.

$0 holds the long path name
```

filename="${0##*/}"
```

sets filename to the basename of $0 (by chopping off everything up to the last forward-slash).

---

### Post by osx on 2009-10-19
> **unutbu said:**
> Perhaps try:
```
find /media/shared \( -iname "*.mp3" -o -iname "*.ogg" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" /home/john/Desktop/Podcasts/"$filename"' {} \;

```
The above command finds all the mp3 and ogg files in /media/shared and runs the command
```

sh -c 'filename="${0##*/}"; ln -sf "$0" /home/john/Desktop/Podcasts/"$filename"'  {}
```

on each file, substituting the long path name for {}.

$0 holds the long path name
```

filename="${0##*/}"
```

sets filename to the basename of $0 (by chopping off everything up to the last forward-slash).

Thanks, that works. I have two more questions if you don't mind.

First, in regards to the "${0##*/}", where do I learn more about that sort of thing? I'm reading "Learning the bash Shell - 2nd Edition" and "Linux Shell Scripting with Bash" and have found nothing in them similar to what you came up with.

Does this have something to do with positional parameters?

Can you recommend any books on bash scripting besides these two?

Second, I am trying to expand the script to look for video files as well and put them in separate directories. Here is what I have:

```
audio=$HOME"/Desktop/Shared-media/audio/"
video=$HOME"/Desktop/Shared-media/video/"
find /media/shared \( -iname "*.mp3" -o -iname "*.ogg" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" "$audio$filename"' {} \;
find /media/shared \( -iname "*.mpg" -o -iname "*.mov" -o -iname "*.avi" -o -iname "*.rm" -o -iname "*.divx" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" "$video$filename"' {} \;
```

However, using "$video$filename" or "$video""$filename" (same goes for the audio path) does not work for the output links. I'm running the script from my desktop and the links always end up on the desktop instead of the path defined.

Obviously the easier solution would be to do what your command has in it and just specify the path in the command, but now that I have tried to do it with variables and can't get it to work, I want to know why it won't work and how to make it work the way I want.

Any suggestions?

This seems like it should be pretty easy to do, but I obviously do not fully understand the mechanics of your solution.

Thanks.

---

### Post by osx on 2009-10-19
Disregard for the moment my question regarding {0##*/}. When I looked up positional parameters in the "Linux Shell Scripting with Bash" book I found an example of it on page 145. I'll study it more there, first.

Thanks.

---

### Post by unutbu on 2009-10-19
osx, perhaps try this:

[PHP]find /media/shared \( -iname "*.mp3" -o -iname "*.ogg" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" "$1"' "$audio$filename" {} \;
find /media/shared/ \( -iname "*.mpg" -o -iname "*.mov" -o -iname "*.avi" -o -iname "*.rm" -o -iname "*.divx" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" "$1"' {} "$video$filename" \;
[/PHP]
I think the problem is that within single quotes bash does not expand the variables "$video$filename" and "$audio$filename".  So if you move them outside of the single quotes, then they become arguments to the single-quoted command. You can then refer to it within the single quotes as "$1". 

I've never managed to read more than a few pages about bash before my eyes glaze over, so I have no first-hand opinion about bash tutorials. I respect geirha's knowledge about bash however, and read recently that he recommends [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide).

---

### Post by osx on 2009-10-25
> **unutbu said:**
> osx, perhaps try this:

[PHP]find /media/shared \( -iname "*.mp3" -o -iname "*.ogg" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" "$1"' "$audio$filename" {} \;
find /media/shared/ \( -iname "*.mpg" -o -iname "*.mov" -o -iname "*.avi" -o -iname "*.rm" -o -iname "*.divx" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" "$1"' {} "$video$filename" \;
[/PHP]
I think the problem is that within single quotes bash does not expand the variables "$video$filename" and "$audio$filename".  So if you move them outside of the single quotes, then they become arguments to the single-quoted command. You can then refer to it within the single quotes as "$1". 

I've never managed to read more than a few pages about bash before my eyes glaze over, so I have no first-hand opinion about bash tutorials. I respect geirha's knowledge about bash however, and read recently that he recommends [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide).

Thanks, but neither of these worked. The closest was the second one, but it created links to the files as though they were directories and they kept repeating themselves.

---

### Post by Barriehie on 2009-10-25
Here's an online tutorial that kept coming up for me when undertaking to understand BASH.  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)  You're doing more than I need but maybe the link will help.

Barrie

---

### Post by osx on 2009-10-25
> **Barriehie said:**
> Here's an online tutorial that kept coming up for me when undertaking to understand BASH.  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)  You're doing more than I need but maybe the link will help.

Barrie

Yeah, that's a really good one. I've been using that for quite a bit now and even have it as a PDF on my laptop for reading when I am not online. I think I'm just trying to do something that most people don't seem to have a need for.

I guess most people would just use a GUI tool, but I like the idea that I could cron this and keep an updated list of available multimedia files at all times. I don't want to have to launch a GUI tool and then wait for the results each time I want to find something.

Thanks.

---

### Post by osx on 2009-10-25
> **unutbu said:**
> osx, perhaps try this:

[PHP]find /media/shared \( -iname "*.mp3" -o -iname "*.ogg" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" "$1"' "$audio$filename" {} \;
find /media/shared/ \( -iname "*.mpg" -o -iname "*.mov" -o -iname "*.avi" -o -iname "*.rm" -o -iname "*.divx" \) -exec sh -c 'filename="${0##*/}"; ln -sf "$0" "$1"' {} "$video$filename" \;
[/PHP]


unutbu, never mind. I should have paid more attention. I ran your second command first and that ended up replacing the original files with broken links. Fortunately, I was working with a test set of data to make my testing go faster.

I replaced the test data with a new set, and tested the first command you suggested on it and it works. The problem with the second command is the placement of the {}.

Thanks, I believe I have what I need to finish now.

---

