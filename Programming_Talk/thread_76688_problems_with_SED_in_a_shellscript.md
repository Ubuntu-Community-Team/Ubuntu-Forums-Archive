---
title: "problems with SED in a shellscript"
date: 2005-10-15
forum: Programming Talk
---

### Post by Thraxes on 2005-10-15
OK, this is what I intend to do: I am working on a DVB streamserver based on VLC. It works great but to start the server, the command with all the needed flags is almost 3 lines long and you have to find out the proper frequency, service ID etc beforehand. All this info though is stored in channels.conf which can be created by the programm "scan" from the DVBtools set. So, I want to make a script where a user can just enter a channel name and the script gets the rest of the data from channels.conf and inserts them into the appropriate flags when calling VLC.

To search the channels.conf I use grep, to filter the fields for frequency, service ID etc I use awk. This works great, as long as the search string in grep follows a certain pattern! I want this script to be as easy as possible to use and want to use sed to format the user input so that grep returns a good result that the rest of the script understands.

Example: User wants to stream CNN, so he enters "CNN" when asked by the script, this entry is then written to a file so sed can be used (pain in the neck that sed doesn't take script variables as input - or does it?). For grep to return a good result this input must be changed to "^CNN:". My sed call to do this would thus be:

> sed 's/^/^/;s/$/:/' $input
$input is the file with the users input

Now, this works nicely but how do I get sed's output into a grep search string? I thought I could use stdout to do this but I have failed so far... any tips? Also what is the best way to store the grep | awk output into a variable?

This is the grep | awk  call and it comes directly after sed
> grep -i "$stdout" ~/channels.conf | awk -F: '{print $2}'

Any tips, this is just my second bash script ever and I sometimes feel that I am in way over my head with this - but learning alot on the way which is nice :D

---

### Post by toojays on 2005-10-15
The cleanest way to do what you want is to put the output of sed into a variable, and then pass that to grep on the command line.```
exp=$( sed 's/^/^/;s/$/:/' $input)
grep -i "$exp" ~/channels.conf | awk -F: '{print $2}'
```

By the way, you can avoid puting your channel entry into a file by using echo to get it into stdin, like this: ```
echo CNN | sed -e 's/$/:/'
```

---

### Post by Thraxes on 2005-10-19
You sir, are the man! It works brilliantly, many thanks!

---

