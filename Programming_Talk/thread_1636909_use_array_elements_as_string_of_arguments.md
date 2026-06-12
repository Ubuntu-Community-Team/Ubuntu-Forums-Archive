---
title: "use array elements as string of arguments"
date: 2010-12-03
forum: Programming Talk
---

### Post by jamesisin on 2010-12-03
I am creating a script to run a command based on an array.  The command has a syntax as follows:

```
command fileUponWhichToAct
```

I am not able to run an iteration over the array because then I have to interact after each file (I would have to click Quit in a dialog as each iteration passed through the command).

```
command "${myarray[i]}"
```

Instead I want to create the command as follows:

```
command element1 element2 element3 ... elementN
```

I tried just handing the array to the command as thus:

```
command "${myarray}"
```

That didn't work.  How can I turn this into what I need:

```
for (( i=0 ; i < ${#myarray[@]} ; i++ )) ; do

   command "${myarray[i]}" ; 
   
   done
```

?

---

### Post by roccivic on 2010-12-03
```
for (( i=0 ; i < ${#myarray[@]} ; i++ )) ; do
  list="$list ${myarray[i]}";
done
command $list

```

?

---

### Post by jamesisin on 2010-12-03
Thanks for the effort.  Your solution doesn't work either.  Depending upon how I arrange my quotation marks I either get one long argument which fails (because each file should be its own argument) or space delimited arguments (which fail because the path/file.names include spaces).

---

### Post by roccivic on 2010-12-03
This will definitely work for absolute paths:

```
for (( i=0 ; i < ${#myarray[@]} ; i++ )) ; do
  list="$list '${myarray[i]}'";
done
command $list
```

---

### Post by jamesisin on 2010-12-03
Yeah, I thought that would work as well.  What I need to get is something like this:

```
command "path to folder/for element 1" "path to folder/for element 2" ...
```

It turns out that my error is before this.  I am getting something like what I outline here, but I am getting an extra slash before the file name (/path/to/file//file.name).  I'm heading out to dinner and will work on this later.

Thanks for helping me think critically.

---

### Post by jamesisin on 2010-12-04
It's something that the Mac is doing.  When I run the find command on my Ubuntu box I get results as expected, but when I run that same find command on the Mac (even though they both run BASh) I get the extra slash before the file name.

Here is the find command as I run it:

```
find "$directory" -type f -name *.[Ff][Ll][Aa][Cc]
```

Is this expected behavior from BASh on the Mac?  Is there a way to alter the find command to remove that extra slash?

---

### Post by Vox754 on 2010-12-04
> **jamesisin said:**
> It's something that the Mac is doing.  When I run the find command on my Ubuntu box I get results as expected, but when I run that same find command on the Mac (even though they both run BASh) I get the extra slash before the file name.

Here is the find command as I run it:

```
find "$directory" -type f -name *.[Ff][Ll][Aa][Cc]
```

Is this expected behavior from BASh on the Mac?  Is there a way to alter the find command to remove that extra slash?

You should quote the regular expression
```
find "$directory" -type f -name '*.[Ff][Ll][Aa][Cc]'
```

Otherwise, bash expands *, matching all files in the current directory, and the result may not work as expected.

Other than that, you should probably show a more complete version of your script. You may be doing some things that make it difficult to process the variables or strings later on.

---

### Post by jamesisin on 2010-12-04
Thanks, Vox.  I appreciate the advice.

When I test the find command on the Mac (or Ubu) I am just running the find command.  The same results appear if I run that command directly as this:

```
find /path/to/folder/ -type f -name *.flac
```

I've never seen find give those double slashes between the path and the file before, but that's how the Mac is giving its results (which is of course not a valid path if I try to hand it to another command).

Adding single quotes to the above command does not alter the output of the find command:

```
/path/to/folder/Jimmy Page - This Guitar Kills (2003) [FLAC] {2cd}/Jimmy Page - This Guitar Kills cd2 1965-1968//06 - Kenny & Deny, Little Surfer Girl.flac

```

---

### Post by Arndt on 2010-12-04
> **jamesisin said:**
> Thanks, Vox.  I appreciate the advice.

When I test the find command on the Mac (or Ubu) I am just running the find command.  The same results appear if I run that command directly as this:

```
find /path/to/folder/ -type f -name *.flac
```

I've never seen find give those double slashes between the path and the file before, but that's how the Mac is giving its results (which is of course not a valid path if I try to hand it to another command).

Why "of course"? Repeated slashes should not hurt. Pathnames like /home/user/file and /home/user//file are equivalent.

Why do you have a slash at the end of the directory, though? find /path/to/folder is how I would write it.

---

### Post by gmargo on 2010-12-04
> **jamesisin said:**
> ```
find /path/to/folder/ -type f -name *.flac
```I've never seen find give those double slashes between the path and the file before, but that's how the Mac is giving its results (which is of course not a valid path if I try to hand it to another command).

That's just because you specified the directory with a trailing slash.  Find builds the destination with something like "dir + '/' + file", so if your directory specification has a trailing slash, then the result will have two slashes.  In Unix, two (or N > 2) consecutive slashes is the same as one.  Note that a path with multiple consecutive slashes is still a valid path.  To fix the cosmetics, try running your find command with a directory without the trailing slash.

---

### Post by jamesisin on 2010-12-04
Ok, here is the script (keep in mind this is not finished):

```
printf "\nHello.\n\n"
read -p "Please provide the root folder under which I will work recursively: "
   if [ -d "$REPLY" ]; then
      printf "\nI have confirmed this is a directory.\n\n"
      directory="$REPLY"
   else
      printf "\nI cannot confirm this is a directory.\n\n"
      exit 1
   fi




## do the work

# parse files into array recursively
 
find "$directory" -type f -name \*.[Ff][Ll][Aa][Cc] > /tmp/whyme

declare -a flacfind
   let i=0
   while read flacline; do
      flacfind[$i]=$flacline
      ((i++))
   done < /tmp/whyme



# use array to build OggS command

for (( i=0 ; i < ${#flacfind[@]} ; i++ )) ; do

   list="$list \"${flacfind[i]}\"" ;

   done

## echo ${list}
## echo "/Users/$USER/Music/iTunes/OggS\ Set.app/Contents/MacOS/Set\ OggS" ${list}

/Users/$USER/Music/iTunes/OggS\ Set.app/Contents/MacOS/Set\ OggS ${list}
   


## clean-up

printf "\n\nI have complete all operations to the best of my ability.\nI will now clean up all files.\n\n"
read -p "Press <ENTER> to coninue. "


exit
```

If I echo the command (OggS) I can copy and paste it into a terminal and it works (see commented line above).  If I run the command in the script it parses the arguments according to space delimitation.

---

### Post by Vox754 on 2010-12-04
> **jamesisin said:**
> Ok, here is the script (keep in mind this is not finished):


Mmm... I don't think you need to do anything special, you just need to take care of quoting.

```
...
# parse files into array recursively
 
find "$directory" -type f -name '*.[Ff][Ll][Aa][Cc]' > /tmp/whyme

declare -a flacfind
let i=0

while read flacline; do
    flacfind[$i]="$flacline"
    ((i++))
done < /tmp/whyme

# flacfind is already an array
myprogram="/Users/$USER/Music/iTunes/OggS Set.app/Contents/MacOS/Set OggS"

"$myprogram" "${flacfind[@]}"

```

With arrays:
```

$flacfind       # first element of array
${flacfind}     # same
${flacfind[0]}  # same
${flacfind[*]}  # entire array as a single argument
${flacfind[@]}  # each element as a separate argument, but they are still separated by spaces

# use quotes to preserve spaces in the elements of the array
"${flacfind[@]}"

```

---

### Post by jamesisin on 2010-12-04
The reason I manipulate the array as I do is to add the quotation marks around each element ("path/to the next/element/file name.flac") so that the spaces don't get in the mix.

I do like the idea of making the command into a variable for neatness' sake, but that's more eleganting and can come later.  For now I need to sort out how to convince the command when run in the script to behave the same as the same command when run outside the script.

I'm not clear why when I run it in the script the quotes are ignored.  I get errors like this:

```
Setting 'OggS' FSType on '"/Users/username/Music/iTunes/iTunes'... failed. (?!)
Setting 'OggS' FSType on 'Music/Hal'... failed. (?!)
Setting 'OggS' FSType on 'Wilmer/Weird'... failed. (?!)
```

You can see that the quotation mark ('"/Users) is included and yet iTunes Music, Hal Wilmer, and Wierd Nightmares are each broken at the space.

Again, when I echo the command and arguments it is correct and I can copy and paste that into a terminal and it works.

---

### Post by jamesisin on 2010-12-05
Vox - I must have had a typo somewhere because I tried it again and got it to work.  I'll be posting the results to my blog probably tomorrow so anyone interested can see it.  I'll add a link here.

---

