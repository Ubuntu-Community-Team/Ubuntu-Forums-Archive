---
title: "Iterating through an array to run a command"
date: 2010-09-30
forum: Programming Talk
---

### Post by jamesisin on 2010-09-30
I have a couple of arrays with lists of paths/to/files which I intend to then use to run a command (*shnsplit*).  This is the structure of the *for* loop I am working with to run those commands.

```
for (( i=0 ; i < ${#albumfind[@]} ; i++ )) ; do
   shnsplit -o flac -f "${cuefind[i]}" -t $trackname "${albumfind[i]}";
   mv "${albumfind[i]}" "${albumfind[i]}".hideme;
   done
```

First I used double-quotes around the array variables but that yielded an error from *shnsplit* (there are two items in the array, hence the two errors):

```
shnsplit: error: need exactly one file to process
shnsplit: 
shnsplit: type 'shnsplit -h' for help
shnsplit: error: need exactly one file to process
shnsplit: 
shnsplit: type 'shnsplit -h' for help

```

The *mv* command works but that's really just fluff.

I then switched to the backticks but that was unproductive.

So I tried just using a simple *ls* command:

```
for (( i=0 ; i < ${#albumfind[@]} ; i++ )) ; do
   ls "${cuefind[i]}"
   done
```

Using double-quotes worked as expected for *ls* and backticks gave odd results.

What am I doing wrong?  Double-quotes, sure, but then why does *shnsplit* do nothing?  Is there a way to get my script to post the command (a verbose mode) so I can make certain I am parsing the correct command when the script builds the *shnsplit* lines?  Other suggestions?

---

### Post by jamesisin on 2010-09-30
Ok, so I figured it out.

The variable **$trackname** contains one of two possible arguments for *shnsplit*.  The contents of this variable must be quoted on the command line.  I thought I would need to quote the contents of the variable as well as quote the variable itself.  Apparently that's not the case.  I am now building that variable thusly:

```

if [ "$REPLY" = "y" ]; then
   printf "\nOk, I'll include performer names: 01 - Performer Name - Track Name.flac\n\n"
   trackname="%n - %p - %t"
else [ "$REPLY" = "n" ]; 
   printf "\nOk, I won't include performer names: 01 - Track Name.flac\n\n"
   trackname="%n - %t"
fi
```

Normally (on the command line) *shntool* requires those quotes.

In short everything in the script is now working...

...except...

For whatever reason, *shnsplit* is saving its output to the folder of my command line location rather than the folder in which it is directed for the two files.  There is a *-d* option for direction, so it looks like I'll be creating yet another array or at least a *for* loop to create those locations.

Suggestions welcome.

---

### Post by jamesisin on 2010-09-30
The final product, for any interested parties:

[http://www.soundunreason.com/InkWell/?p=2485](http://www.soundunreason.com/InkWell/?p=2485)

---

