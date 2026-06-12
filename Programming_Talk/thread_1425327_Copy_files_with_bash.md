---
title: "Copy files with bash"
date: 2010-03-08
forum: Programming Talk
---

### Post by legolas on 2010-03-08
First, let's keep the laughter to a minimum:P
I am not very good at Bash, but I am trying to figure out how to copy many files from one directory to another on an external hard drive.
I have dinked around for about a week or so and am in need of some direction.
I have the names of the files I want to copy in a file and figured out how to get them to line up separated by a space and in quotes:

echo $(cat files)

but when I try something like this:

cp $(cat /home/me/filenames) /media/"My Passport"/folder/

but that did not work so I tried something like this:

for name in "$VIDS"; 
do   cp -- /media/folder/{$name} /media/"My Passport"/folder/; 
done

but it takes all the multi-word file names and breaks them up into single file names and errors out.
for example it takes the first file named "file number one.txt" and says
"file"
"number"
"one"

I need help figuring out how to get /media/omega/somefiles to  /media/"My Passport"/folder/ by getting the file names I want to copy from a list.

Any pointers? 
They are greatly appreciated.

---

### Post by fulgencio on 2010-03-08
Have you tried 
cp /media/omega/somefiles/*.* /media/"My Passport"/folder/

not sure I understand your question though, why do you need anything else than just the command cp?

---

### Post by deer dance on 2010-03-09
I'd recommend you use **cp /media/omega/somefiles/*** rather than ***.***

This way it catches all files, with or without a period in them.

---

### Post by legolas on 2010-03-09
I am talking about many files so I need to get the certain ones I need to copy from a list of file names and then pipe it to cp somehow.

---

### Post by schauerlich on 2010-03-09
Sounds like a job for xargs.

```
cat foo | sed 's/ /\\ /g' | xargs -I SRC cp SRC dest/
```

Replace foo with the list of files you made, and dest/ with the destination folder.

This will replace all of the spaces in the file with '\ ', which will keep xargs from separating "empire strikes back" into "empire" "strikes" "back". It then sends the list of files to xargs, which hands the arguments to cp.

---

### Post by DaithiF on 2010-03-09
```
while read filename
do
  cp "$filename" /path/to/destination/
done < filenamelist

```

---

### Post by d3v1150m471c on 2010-03-09
```

rsync -a /the/folder/with/contents /media/external

```
This will only add files that don't exist in the destination folder that do exist in the source folder.

---

### Post by legolas on 2010-03-09
Thank you guys so much for all the responses.  Since I need to read them from a list because I don't want to copy all of the files, I think what DaithiF suggested is the closest to what I need.
The list of filenames are relative, so to get the absolute path, would it be correct grammar if I did something like this?

while read filename
do
  cp /media/folder/"$filename" /path/to/destination/
done < filenamelist

Also, waht does the last bit do:  done < filenamelist     ???

---

### Post by DaithiF on 2010-03-09
> 
while read filename
do
  cp /media/folder/"$filename" /path/to/destination/
done < filenamelist


that will work, but personally I think:
cp "/media/folder/$filename" looks neater

the done < filename part is a form of input redirection.  The while loop reads a line at a time, and the < filename tells it where to read data from.

---

### Post by legolas on 2010-03-10
Thanks again.
I tried this:

filename=$(cat /home/me/filenames)


while read filenames
do
cp /media/omega/"$filename" /media/"My Passport"/michael/
done < filenames 


buuuuut, it strung all the filenames together in to one big filename and ended with the error "File name too long"

I am supposing I need to quote all the filenames.  How could I work that into my little script?

I tried to pipe it to ls -Q but I could not get the grammar right and error'ed it up and down.

---

### Post by schauerlich on 2010-03-10
Did you try my solution?

---

### Post by d3v1150m471c on 2010-03-10
< filenamelist is telling the command to import the paths from the file named "filenamelist"

---

### Post by DaithiF on 2010-03-10
> **legolas said:**
> I tried this:

filename=$(cat /home/me/filenames)


while read filenames
do
cp /media/omega/"$filename" /media/"My Passport"/michael/
done < filenames 

No.  Sorry if the previous post wasn't clear enough -- maybe this will make it clearer:
```
while read hello_i_am_an_arbitrary_variable_name
do
cp "/media/omega/$hello_i_am_an_arbitrary_variable_name" "/media/My Passport/michael/"
done < /home/me/filenames
```

---

### Post by legolas on 2010-03-10
Holy cow, its working!  Thanks guys.  
schauerlich, I am sorry, but your solution is way above me- I don't understand it at all so I was scared to try it.

As far as
done < filenames 
goes, shouldn't that have to be in the begining?  I mean, if it is doing the comands in order, if cp comes first, how can it know what filenames to copy if the imput comes second?
Oh, just looking at it again, is that all one line of commands like this?:
while read variable do cp "/media/omega/$variable" "/media/My Passport/michael/" done < /home/me/filenames


If that is the case, I think I get it.

Also, why the quotes on just the cp files and destination parts, but not on the done < /home/me/filenames part?

Thanks again. BASH is cool, and so are you guys.

---

### Post by DaithiF on 2010-03-10
> **legolas said:**
> 
Also, why the quotes on just the cp files and destination parts, but not on the done < /home/me/filenames part?

quotes are only required where filenames / paths may have spaces in them.

---

### Post by legolas on 2010-03-10
So, I have heard of sed, but what is xargs?  schauerlich, your code looks really neat.  What is with all the slashes?  Is that still bash?
Man, I need to study more.  Every thing I know is from books.  Do you guys think it is a good idea to go take some community college courses to get this programming thing down?  How did you guys learn?

---

### Post by schauerlich on 2010-03-11
> **legolas said:**
> So, I have heard of sed, but what is xargs?  schauerlich, your code looks really neat.  What is with all the slashes?  Is that still bash?

I'll break it down for you.

```
cat foo
```
Put the filename list in stdout

```
sed 's/ /\\ /g'
```
Change all occurrences of ' ' to '\ '. This makes it so that multiword filenames don't get broken up. To bash, ~/videos/empire strikes back looks like 3 things - '~/videos/empire', 'strikes', and 'back'. Changing the ' ' to '\ ' makes it read ~/videos/empire\ strikes\ back, which bash reads as '~/videos/empire strikes back'

```
xargs -I SRC cp SRC dest/
```
Run 'cp SRC dest/' on each file in the filenames list, replacing SRC with one filename.

---

