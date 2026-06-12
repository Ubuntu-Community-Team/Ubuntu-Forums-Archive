---
title: "awk help, new to awk"
date: 2020-03-06
forum: Programming Talk
---

### Post by getut on 2020-03-06
I'm trying to use awk to edit an xml file. I'm using awk instead of sed because ultimately this is purposed for a non-ubuntu, non-debian OS and there are limitations to the freebsd sed where this ultimately needed.

In my environment awk is more portable from my testing platform to the final usage than sed.

It is a rather large xml file but the gist of it is that I have a unique line that is my search line, directly followed by the line that I actually need to change. The source for the change will be coming from another file that contains ONLY the entire line that needs to be changed.

So the 2 line block in the file that needs to be changed would be similar to:

     <unique_xml_tag>data1,data2</unique_xml_tag>
     <custom_tag>encrypted data that needs to be changed</custom_tag>

The extra file contains ONLY the line
     <custom_tag>different encrypted data</custom_tag>

Just playing with this and trying to break this down into logical learning steps. I am past the step of simply identifying the line I need to change. But I'm getting something way wrong trying expand on it and work this into some version of the sub command.

awk '/unique_xml_tag/ { getline; print }' file_to_be_edited.xml 

is spitting out the line that I need to change. But the rest of my needs are beyond me so far.

I have tried reading my changes into a variable with awk -v changes=`cat file_containing_changes.txt` but that doesn't seem to work. Also for the actual substitution itself I've been playing with awk sub and can get it to work replacing the first line that I match to, but getting sub to work with getline so that it takes place on the second line is also too much for me at this early stage.

I just can't pull it together into a working command and I can't find any examples of quite this type of scenario. I found getline into a variable from a file, I found replacing from secondary files, but nothing quite like this to use as an example.

---

### Post by spjackson on 2020-03-07
How about something like this?
```

# Replace the line following unique_xml_tag with the contents of /etc/motd
awk 'BEGIN { target=-1 ; }
/unique_xml_tag/ { target = NR+1 ; }
{ if (NR==target)
    system("/bin/cat /etc/motd") ;
  else
    print $0 ;
}
'

```

---

### Post by getut on 2020-03-09
Thanks for this! You got me going but I want to ask some questions about it to make sure I understand and learn.

In the first target=-1 you are actually setting that the value -1, not any line of text? And that is for the purpose of forcing the if/else block to fail if the value doesn't get properly set?

The part I don't understand what is going on is this part:
/unique_xml_tag/ { target = NR+1 ; }
{ if (NR==target)

You are setting the target var to the row after nextrow (NR+1) but then immediately testing if NR equals target. If target is set to the row AFTER the next row, how does it ever equal the next row?


Edit: I've even played with this some more trying to figure out what the very first line does... if it is just a number or if it is the contents of the line itself. If I set the first line to 1, the added data gets stuck into what seems to be an absolute position at line #1. If I put 10 the changed data get stuck in line number 10. But when set to -1 the data gets stuck into the correct position like it is a RELATIVE location. But setting the number to -2 or -20 does not change it. It still gets stuck in the correct position.

This simple command seems to be doing magic that I still don't understand.

---

### Post by spjackson on 2020-03-09
> **getut said:**
> Thanks for this! You got me going but I want to ask some questions about it to make sure I understand and learn.

In the first target=-1 you are actually setting that the value -1, not any line of text? And that is for the purpose of forcing the if/else block to fail if the value doesn't get properly set?

The part I don't understand what is going on is this part:
/unique_xml_tag/ { target = NR+1 ; }
{ if (NR==target)

You are setting the target var to the row after nextrow (NR+1) but then immediately testing if NR equals target. If target is set to the row AFTER the next row, how does it ever equal the next row?


Edit: I've even played with this some more trying to figure out what the very first line does... if it is just a number or if it is the contents of the line itself. If I set the first line to 1, the added data gets stuck into what seems to be an absolute position at line #1. If I put 10 the changed data get stuck in line number 10. But when set to -1 the data gets stuck into the correct position like it is a RELATIVE location. But setting the number to -2 or -20 does not change it. It still gets stuck in the correct position.

This simple command seems to be doing magic that I still don't understand.
NR is an awk built-in variable that contains the current line number,  starting at 1. So ```
awk '{print NR, $0}'
``` would output all the lines of the input file with each line being preceded by the line number  (similar to 'cat -n').

Suppose /unique_xml_tag/ matches when NR is 4 (i.e. on  the 4th line of the  file), then 
```

target = NR+1
``` sets 'target' to 5. When the next line is processed, NR is now 5  so ```
if (NR==target)
``` is true. For subsequent lines, it is false again - unless  /unique_xml_tag/ appeared again in the file, in which case we'd do the replacement again on the next line.

```
BEGIN { target=-1 ; }
```
I'm a programmer, so I initialise my variables unless I know the  language well enough to fully understand what happens if I don't. I chose -1 because NR is never negative, so I know that the 'if' expression will always be false until /unique_xml_tag/ matches and then we set target to be the actual line number that we want to change. If target is  uninitialised, what will the result of that 'if' expression be? I don't know  since I don't know awk well enough. I'd rather initialise target so I  can be sure. Experimentation now shows that it's probably not necessary, but I don't know whether that behaviour is predictable across all awk implementations. An awk expert might be able to tell us.

---

### Post by getut on 2020-03-09
Ahh thank you very very much! I had even read the docs for NR and did not understand that it was the LINE NUMBER. I thought NR meant the text content of the nextrow. So if you match on the regex NR would be the content of the next row, not a line number for either the current or next row.

It makes sense understanding that NR is an actual number now.

---

