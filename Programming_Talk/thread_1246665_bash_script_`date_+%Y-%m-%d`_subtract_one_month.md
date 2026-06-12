---
title: "bash script `date +%Y-%m-%d` subtract one month"
date: 2009-08-22
forum: Programming Talk
---

### Post by shane2peru on 2009-08-22
Ok, I have a cron job to record an internet radio show that I enjoy.  However I manually end up having to go and delete these recorded shows.  So I decided to get fancy and write a cron job to remove the old shows.  Here is what I have:
```

0 10 10 * * rm /home/user/location/show-`date +%Y-%m`-0*
0 10 20,21,22 * * rm /home/user/location/show-`date +%Y-%m`-1*
0 10 30,31 * * rm /home/user/location/show-`date +%Y-%m`-2*

```
ok, I generi-sized that a bit, but you get the idea.  Those should work fine, my problem is I get day's 30 and 31 that hang there and collect.  So I would like to use the ```
show-`date +%Y-%m`-3*
``` for the previous month and remove them.  I don't really want to write 11 code lines to delete them and crontab it out as that would be excessive.  Is there a way to use the previous month in a string format for this type of stuff?  Or can the string be used subtracting one month?  Or do you have a better idea?  I'm no programmer, but have greatly enjoyed learning scripting, so if it can be done with bash it is better, not over my head. :)  Thanks.

Shane

---

### Post by slavik on 2009-08-22
find is a useful command. below is an example you can use to delete files in a directory that were last modified more than 30 days ago.
```

find /dir/where/shows/are/ -mtime +30 -exec rm {} \;

```

---

### Post by mobilediesel on 2009-08-22
> **shane2peru said:**
> Ok, I have a cron job to record an internet radio show that I enjoy.  However I manually end up having to go and delete these recorded shows.  So I decided to get fancy and write a cron job to remove the old shows.  Here is what I have:
```

0 10 10 * * rm /home/user/location/show-`date +%Y-%m`-0*
0 10 20,21,22 * * rm /home/user/location/show-`date +%Y-%m`-1*
0 10 30,31 * * rm /home/user/location/show-`date +%Y-%m`-2*

```
ok, I generi-sized that a bit, but you get the idea.  Those should work fine, my problem is I get day's 30 and 31 that hang there and collect.  So I would like to use the ```
show-`date +%Y-%m`-3*
``` for the previous month and remove them.  I don't really want to write 11 code lines to delete them and crontab it out as that would be excessive.  Is there a way to use the previous month in a string format for this type of stuff?  Or can the string be used subtracting one month?  Or do you have a better idea?  I'm no programmer, but have greatly enjoyed learning scripting, so if it can be done with bash it is better, not over my head. :)  Thanks.

Shane
I came up with this for you:
```
show-`date +%Y-%m --date="last month"`
```
Then Slavik came up with the superior:
> **slavik said:**
> find is a useful command. below is an example you can use to delete files in a directory that were last modified more than 30 days ago.
```

find /dir/where/shows/are/ -mtime +30 -exec rm {} \;

```
There's no real script required for that, just put that in your crontab.

---

### Post by shane2peru on 2009-08-22
Thanks both of you!!!  I will use them.  Bash script was more of a description of what I wanted.  At any rate, I can really modify the find one to fit my needs and anything that is seven days old can be deleted with one line. :)  Thanks!!!

Shane

---

