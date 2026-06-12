---
title: "How to increment an output filename in bash"
date: 2010-05-08
forum: Programming Talk
---

### Post by hellocatfood on 2010-05-08
I'm currently working on this script to do random edits on a video [http://dpaste.com/hold/188378/](http://dpaste.com/hold/188378/) I want to do multiple edits of the same video and output them as different filenames automatically.

For example, instead of having to change the output filename in the script manually, everytime I run the script I want it to output file001.avi, file002.avi file003.avi etc.

Is there a way I can do this in bash? I know that people have recommended using the date, but I need the files to be sequential

---

### Post by s1ightcrazed on 2010-05-08
Do you plan on running the script multiple times, or is it going to just be run once and it will output all the files at that time? 

If running it multiple times, I would have it grab the 'newest' file in the directory, and use cut to grab the sequence number of the file. So the script will have to know that the first run creates the 'file001.out' and then it reads that file on the next run, sees the '001' and increments it to 002...and so on and so forth. 

last_file_sequence_number=$(ls -tr | tail -1 | cut -c 5-7)
new_file_sequence_number=$(($last_file_sequence_number+1))
new_file_name=file${new_file_sequence_number}.out

if you're only running the script once but outputting multiple files, then you can just keep track of the sequence locally, and do $((seq=seq+1)) to increment it each time. 

Enjoy.

---

### Post by hellocatfood on 2010-05-08
I think I'll have to opt for the latter option. Do you have an example of how that code is implemented? I'm still learning bash (that code you saw took at least 5 hours to make!)

I know that it'll involve for loops to decide how many times to run the script, but after that I'm a bit lost

---

