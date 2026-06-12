---
title: "while loop with more than one line at a time"
date: 2011-10-26
forum: Programming Talk
---

### Post by bcooperizcool on 2011-10-26
What I am wanting to do, is do a while loop sort of thing, for a file, but read more than one line at a time, and tell it to read only between two points at a time.


So file1 contains:
```
<dict>
      <something>Hello</something
      <key>KEY!</key>
      </dict>
      <dict>
      <something>rawr</something>
      <key>label</key>
      <string>Title</string>
      <key>Something else</key>
      <string>Hello</string>
      <dict>
```

I have other files that I am going to read like this, as variable

```
hello=$(</var/mobile/hello)
      rawr=$(</var/mobile/rawr)
```

the contents of these are <dict>contents of the thing</dict> that match <dict> </dict> of their respective parts in the file.

so I want to use this code (well, something that works, as this does not :P):
```
while read variable; do
      if [[ "$variable" == "$rawr" ]];
         then echo "rawr" >> "list";
      elif [[ "$variable" == "$hello" ]];
         then echo "hello" >> "$list";
      else some_handler_code_to_make_new_variable_with_contents_of_dict;
      fi
```

to echo the name into a separate file.

Edit:

or possibly some way to check the lines against each other one at a time?   but I would need the end result of the <dict> </dict> still :/


Thanks!

---

### Post by ofnuts on 2011-10-27
Use grep with -A and -B arguments to extract the context of what you found: For instance; given your structure:, to find the <string> which is after the <key>, something like:

grep "<key>$key" -A 2 $dictfile | grep "<string>"

Edit: looking in the dict file for every key you encounter isn't going to be good for perfs. I would suggest to first read the dictionary in an associative array (new in Bash 4). It works like this:

```

#declare variable as array
declare -A dict
# Initilize aray
key='SomeKey'
value='SomeString'
dict=([$key]=$value)
# Let's retrieve something
laterKey='SomeKey'
echo ${dict[$laterKey]}
***SomeString***

```

---

### Post by bcooperizcool on 2011-10-27
Thanks for the reply!   I have a question though, is does this run the code for each sets of <dict></dict> it finds?

I am basically have sets of files each containing a <dict></dict>, with the type it is (or name for it).   If it encounters one it does not know, it looks for a label (I can code that), and makes a new entry file for it.


So it is identifying the types and then putting them into a text file that goes like this:
```
Power
      Brightness
      Sounds
```

and whatnot.   where each of these entries is also the name of a file that contains the code for the <dict></dict>

---

### Post by ofnuts on 2011-10-27
> **bcooperizcool said:**
> Thanks for the reply!   I have a question though, is does this run the code for each sets of <dict></dict> it finds?

I am basically have sets of files each containing a <dict></dict>, with the type it is (or name for it).   If it encounters one it does not know, it looks for a label (I can code that), and makes a new entry file for it.


So it is identifying the types and then putting them into a text file that goes like this:
```
Power
      Brightness
      Sounds
```and whatnot.   where each of these entries is also the name of a file that contains the code for the <dict></dict>
That's up to you... the question is how any times you are going to search keys in each file. If you have one single file from which you will retrieve keys 200 times, making a dictionary array in bash will help. If we are talking about several dictionary files with only a few keys in each, the grep-based method should perform almost as well.

---

### Post by bcooperizcool on 2011-10-27
Sorry for being thick, but I only want this to return one result at a time, and check against a list of things to see if it is a match.   There are multiple results in the file though.    Will this be able to handle that?


I am not near a linux machine for a while still, so I can't test yet, so that's why I am asking.

---

### Post by ofnuts on 2011-10-27
> **bcooperizcool said:**
> Thanks for the reply!   I have a question though, is does this run the code for each sets of <dict></dict> it finds?

I am basically have sets of files each containing a <dict></dict>, with the type it is (or name for it).   If it encounters one it does not know, it looks for a label (I can code that), and makes a new entry file for it.


So it is identifying the types and then putting them into a text file that goes like this:
```
Power
      Brightness
      Sounds
```and whatnot.   where each of these entries is also the name of a file that contains the code for the <dict></dict>
That's up to you... the question is how any times you are going to search keys in each file. If you have one single file from which you will retrieve keys 200 times, making a dictionary array in bash will help. If we are talking about several dictionary files with only a few keys in each, the grep-based method should perform almost as well.

---

