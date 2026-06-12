---
title: "Automatically working through directories and printing results to file"
date: 2013-05-29
forum: Programming Talk
---

### Post by Mattaus on 2013-05-29
Hi all,

I know next to nothing about bash programming but I have had a crack at something for my media PC.

What I'm trying to do is, on start-up, automatically create a list of the latest episode of each TV show that has been added to the PC. Currently my script removes the old list, creates a new text file, manually determines the last added episode in each TV show directory and then adds it to the list. When I say manually, I mean I have added a line for each and every TV show:

```
ls -Art /location_of media/tv_show_one/* | tail -n 1 >> $latest_episodes.txt
ls -Art /location_of media/tv_show_two/* | tail -n 1 >> $latest_episodes.txt
ls -Art /location_of media/tv_show_three/* | tail -n 1 >> $latest_episodes.txt

...and so on.
```

Now this is fine....except I have 27 different TV shows, each with their own directory, and this is being added to on a regular basis. I would like something more robust - something that when given a starting directory can work its way into each sub-directory, recognize when it can't dig any deeper and then determine the latest file in that directory. Once it's done this is starts back at the top and moves onto the next directory. It would do this until it's gone through all the directories in the starting directory that was given to it.

Is this something that can be done? Is it worth it? 

I've started reading and Googling but it's getting late where I am, I'm tired and I need to hit the sack. Just casting a net out to see if I can get a little bit of a head start on this tomorrow :)

Thanks,

- Matt

---

### Post by epicoder on 2013-05-29
There are a couple methods of doing this. Which you use depends on how your shows are organized.
If you use a known starting location and path depth, then this becomes very simple:
```
for x in $(ls location_of_media); do
  ls -Art "$x" | tail -n 1 >> latest_episodes.txt
done
```
Skipping over files in the same directory as your show folders is also simple:
```
...
  if [ -d "$x" ]; then
    ls -Art ...
  fi

```

However, if you have differing path lengths (this tree for example)...
```

show_1

show_2

shows_I_like
 |-- show_3
 +-- show_4

shows_I_need_to_catch_up_on
 |-- show_5
 +-- show_6

```
...then you'll need to write a path walker. I'll leave that as an exercise to the reader.

---

### Post by TheFu on 2013-05-29
I'd be shocked is there isn't already python or perl script that does this.  Something related to mythtv or torrenting tools in your searches might provide more results.

As for your script, why not just use a loop?  Bash does this easily. [http://tldp.org/LDP/abs/html/loops1.html](http://tldp.org/LDP/abs/html/loops1.html)  That link will teach you the mechanics of bash scripting. Along with the man page for bash, I think 99% of what people need to know is covered.

For the loop, you can either provide a list of directories or have the script generate that list using file globbing.
Don't be afraid to ask questions, but please post very specific scripts that aren't working when you do.

The use of **ls -t** is fine, but if you can guarantee that only 1 show will be added a day, then using **find** with a **-mtime** option might be better.  I don't know - both can work.
**find . -mtime -1** is an example that looks for any files modified in the last day from the current directory down.  

A little more specifics is:
**find /Data/TV  -mtime -1 -a -type f -iname \*wtv**
* Look from /Data/TV down.
* modified in the last day
* only look for files (not directories)
* use case-insentive file globbing ... basically files that end in wtv or WTV or WtV or wTV .... will be listed.

Then using **dirname** and** basename** to keep the directory and know where to shove the last files into a list should be easy AND fast.

---

### Post by steeldriver on 2013-05-29
Your best bet is probably the 'find' command

```
find Documents/ -type f -newermt "18 May 2013"
```

or with a relative date and printing just the file name (without the path)

```
find Documents/ -type f -newermt "$(date --date='3 days ago')" -printf '%f\n'
```

or a bit of a hack, to find the single newest plain file in each directory (i.e. ignoring newer subdirectories, if present), you could do something like

```
find Documents/ -type d -execdir sh -c "ls -1tp {} | sed -n '0,/[^/]\+$/ s//&/p'" \;
```

---

### Post by Mattaus on 2013-05-29
OK, I will have to try some of this tonight. Just to be clear on a few things:

[LIST]
[*]My tv_show directory contains a sub-directory for each show. There are **no** sub-directories under these show directories. Basically > /var/media/tv_shows/show1...show2....show3...etc
[*]Multiple shows can be added per day, but normally only one episode for each series.
[*]I want to know what the last episode added was for every show, regardless of whether it had a new show added since the previous update or not.
[*]File extensions are random. They could be anything. But this is irrelevant (I think) because all I am really interested in is the date stamp on the file.
[/LIST]

I'm actually using Openelec on my HTPC, but seen as I'm a member here and it's all basic scripting I figured I would ask here first before signing up to yet *another* forum. Openelec does in-fact show the last media added, however I'm creating this script for something else that the in-built Openelec functionality does not do quite right for my purposes.

I'll try the first method suggested because it seems the simplest and I more-or-less understand what it's doing. That being said, the linked provided by TheFu is gold, and probably worth a read for my own education...so thanks for that :)

Lets see how I go!

Cheers,

- Matt

---

