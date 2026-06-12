---
title: "Iterate files in a directory by date created in Perl"
date: 2009-03-08
forum: Programming Talk
---

### Post by Medieval Cow on 2009-03-08
Ok, so the title pretty much explains what I need to do. I've googled a bunch for this, but I can't find anything. I'm running through all the files in a directory, and it looks like by default it's just going through by file name in alphabetical/numerical order. Here's what I've got grabbing the file names:

```
$directory = "/var/lib/mythtv/recordings";

# Iterates through the directory picking out all the .MP4 files
foreach $f (<$directory/*>) {
    if ( $f =~ /\.mp4$/ ){
        $f =~ s/\.mp4$//;
```

I scavenged that from a script I found that I run along with [MythTV for iPhone]("http://chriscarey.com/projects/mythtv/iphone/") that runs through to clean up any MP4 files after you delete the original recording to keep the directory tidy. Anyway, what I'm doing with it after that is setting up an iTunes-compatible RSS feed so my transcoded files will automatically download into iTunes on my Windows box, and so I can download them directly to my iPhone via [RSS Player]("http://rssplayer.blogspot.com/") so I can watch them even if I don't have a great signal.

In the spirit of open source, I plan on posting the script in the MythBuntu forum in case anyone else wants to do the same thing I am. I just want to iron a few things out first, and this is one of them. The file names look like this: 1048_20090301180000.mpg.mp4. Those digits all signify things. I believe the first two are what tuner you're using or something like that. The next two are the channel. Then after the underscore is the year, month, day, time. So if everything is recorded on the same channel, I end up with the oldest recordings at the top of the feed, and the newest at the bottom. I'd like to reverse that. That'd be easy enough to just save them as strings or in an array or whatever, and then write them out in the reverse order they were created after it's done running through all the files in the directory. However, when something is recorded on a different channel, it throws a monkey wrench in there. I'd like to get the newest recording at the top so it works with the most feed readers. iTunes handles it ok as it is, but RSS Player gets a little wonky when the newest file isn't at the top. I'd imagine other readers would probably have issues with that too.

So is there an easy way to just iterate through those files in the (reverse) order they were created? Or am I just going to be stuck grabbing the date out of them with regular expressions to manually sort them that way?

Bonus question: the script I run that transcodes the files to MP4 format is a bash script that's called automatically by MythTV after the recording completes. Is there any way I can then have that bash script call my Perl script after it's done? Right now I just have a cron job running it once a day, but I'd love to have it automatically generate the feed as soon as a new file is added.

---

### Post by geraldm on 2009-03-09
the command line statement might be
ls -lu --sort=time *.mp4

not doing perl, but a ruby way might be:

a = IO.popen("ls -lu --sort=time *.mp4")
bb = a.readlines
#{ do something with the array now in bb }

perl would have some equivalent methods, as even ruby has more elegant methods.
Start by reading man page for "ls".
In the bash man page look up "exec <path_to_script>" so you know that you are exiting the bash script at that point.

regards,
Gerald

---

