---
title: "Nautilus Script Environmental Variable Problem"
date: 2008-04-30
forum: Programming Talk
---

### Post by aarb00 on 2008-04-30
I am trying to create a simple script using Environmental Variables to pass commands to HandBrake.  I figured this would be an easy first script to write but am having some problems with the variables and a good approach to troubleshooting.  

Here is what I have done so far:

After right clicking on a folder, you are prompted for a movie name, this line works but puts what I think is a line feed character at the end of the movie name.  How can I get rid of the character in code?

movie=$(zenity --entry --text "What is the name of the movie to

convert?" --entry-text "${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS##*/}")


So now I have the name properly set in a variable called movie and this brings up two problems.  If you right click on a folder with an underscore, such as VIDEO_TS, both of these lines show VIDEOTS with the T underlined.  In works perfectly for single and multiple word folders even with spaces.


zenity --entry --text "$movie"

zenity --entry --text "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

This brings up my third problem.  I don't need these lines and just used them for troubleshooting, but I don't know if this is the actual information that would be passed to HandBrake.  I know these are Nautilus scripts, so they are GUI scripts, but all of the Nautilus scripts I have seen start with 

#!/bin/bash or #!/bin/sh 

indicating to me that they are passing commands to the terminal, which HandBrake is a terminal program.  So, how can I have my Nautilus script show the output in a terminal?  This would help in troubleshooting, plus allow me to keep an eye on the progress of the encode, which I wouldn't normally get.

Perhaps off topic, but I know Zenity has a progress bar.  Is there anyway the Zenity bar could accept input from Handbrake and provide a status?

Thanks in advance for any help.

---

### Post by aarb00 on 2008-05-01
Bump

---

### Post by mssever on 2008-05-01
I'm not sure exactly what you want to know. You ask some questions, then you seem to suggest that you've solved them yourself.

There's no such thing as a Nautilus script, per se. Any executable you put in the Nautilus scripts folder is a potential script, regardless of the language.

For debugging, first try starting Nautilus from the terminal, so that you can see stuff that Nautilus outputs. If you echo stuff from a bash Nautilus script, you might get output that way. If not, write yourself a simple Bash test harness that simulates Nautilus calls (setting environment variables, etc.

If I didn't answer your question, please clarify it.

---

### Post by aarb00 on 2008-05-02
Thanks for responding.  I think I get the confusion on why you thought I may have solved my problem, but I didn't.  However your response gave me an idea, which I hope can provide more information to get my problem resolved.

I made the statement “So now I have the name properly set” which I only do if I rename what shows up in the dialog box.  The dialog does show the strange character.  

So problem number 1:  Can anyone test my code and tell me what that character is and advise on how I can get it to not show up?

If I hit backspace, the character goes away, leaving me with the proper movie name in the movie variable.  This leads to problem number 2.

If the folder I select to start the Nautilus script is VIDEO_TS, then the next two dialog boxes (which are for testing purposes only) display VIDEO_TS as VIDEOTS with the T underlined.  

Now the 2nd line of code displays $movie and the 3rd line of code uses the environmental variable and they both display VIDEOTS with the T underlined.  It makes no difference whether or not I remove the strange character and the end of VIDEO_TS either.  So the problem with the underscore seems to be with something other than my code, but I am not sure what.

Now because of the message from msserver, I decided to drag and drop my job into a terminal to see what it would do.  Now when it prompts me for a movie name (the field is blank because I didn't right click on a folder), I type in VIDEO_TS, and on the next two lines it returns VIDEOTS with the T underlined.  

Now I would think that this is a bug, but there is a Nautilus Script tool called Nautilus Debug, and when I right click on the folder called VIDEO_TS, it brings up all of the environmental variables, and it displays VIDEO_TS correctly.

Needless to say, I am very confused.

---

### Post by mssever on 2008-05-02
So I can test your code, please post it (in [noparse]```

```[/noparse] tags, please). I don't understand what you mean by "strange characters." The first line of code you posted looks odd, what with the line breaks, etc. Using [noparse][code][/noparse] tags wil prevent the forum software from messing up your code. (If your code really is spread across multiple lines like that, then maybe that's part of the problem.)

As far as the underlining goes, it sounds like zenity interprets an underline as an escape character meaning underline the next character. You'll need to study the zenity docs to find out how to change that behavior. I haven't done very much with zenity.

---

### Post by aarb00 on 2008-05-02
```
movie=$(zenity --entry --text "What is the name of the movie to convert?" --entry-text "${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS##*/}")
```

I was thinking the same thing with Zenity, but I got proper results using the  Nautilus-Script-Debug program, which uses Zenity to display the output.  I attached my code so you can see the character.  

Thanks again.

---

### Post by mssever on 2008-05-02
> **aarb00 said:**
> I attached my code so you can see the character. 

But you didn't attach it in a usable form. I had to write a wrapper to test it. Next time, when you post a test case, post it in a form that can be directly run. Here's the wrapper I wrote: ```
#!/bin/bash
result="$(zenity --entry --text "What is the name of the movie to convert?" --entry-text "${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS##*/}")"
zenity --info --text="$result"
```
That environment variable is set to a newline-delimited list of selected filenames. So, the character you're seeing is \n. You'll need to strip it. Really, you need to handle the case where more than one file is selected, because that could happen.

Here's a test tool I wrote to help me write Nautilus scripts. It shows what the various values look like: ```
#!/bin/bash

zenity --info --title=Environment --text="$(env)"
zenity --info --title="Command Line Arguments" --text="$*"
```


Finally, here's an example script I wrote. Note that when parsing is non-trivial, I usually abandon bash (I've never learned parameter expansion. Maybe that would simplify parsing). ```
#!/usr/bin/env ruby

# Get the currently-selected files as an array
files = ENV['NAUTILUS_SELECTED_FILE_PATHS'].to_s.chomp.split "\n"

if files.length >= 1
  # One or more files must be selected
  `feh #{files.join ' '}`
else
  # no files are selected
  `feh #{ENV['NAUTILUS_SCRIPT_CURRENT_URI'].gsub(/^[^:]+:\/\/(.*)/, '\1')}`
end
```

As for your other issue, you should probably look at the source of Nautilus Script Debug to see what it does.

---

### Post by aarb00 on 2008-05-02
Sorry about the code, but your code worked fine.  The difference was in the zenity command.  You used --info while I used --entry, that took the underline away and gave me a proper underscore.

I'll see what I can do regarding the \n.  Thanks for identifying it for me.  That should make it easier to work out.  

I'll try to make sense of your other code regarding parsing.  I am not up to that level yet, but I am sure I will soon.

The other script you attached is very similar to the Nautilus-Script-Debug I downloaded online.  The reason it gave the correct response was also the --info.

Thanks again, very helpful.

---

### Post by mssever on 2008-05-02
By the way, be sure to quote variable assignments. Your code had something like ```
movie=$(stuff)
```
Instead, use ```
movie="$(stuff)"
```
If the result of the command substitution contains spaces, you'll end up with a result you don't want unless you also use double quotes.

---

### Post by aarb00 on 2008-05-03
I now have a working script and wanted to post it in case anyone was following this thread.  I used different variables which worked out much better, though I am not sure why.  

Using these variables prevented the \n from showing up.  It also eliminated problems I had with spaces using the environmental variables; using quotes didn't help.  The variables weren't passed correctly to HandBrake.

The first section of the script determines the name of the folder you right clicked on.  I did this because Totem won't play any folder other than a VIDEO_TS folder.  This code renames your folder to VIDEO_TS and plays the video in Totem so you can see what title you want to encode.  When you quit Totem it renames it back to what it was before.

This script is useful for those who keep VIDEO_TS folders on their servers so they can quickly make Zune or iPod compatible files and save them to their local machines that they use to sync with.

```

#!/bin/bash

if [ "$*" != "VIDEO_TS" ]; then
mv "$*" "VIDEO_TS"
fi

totem "VIDEO_TS"
mv "VIDEO_TS" "$*"

name=$(zenity --entry --text "What is the name of the movie to convert?" --entry-text "$*")

title=$(zenity --entry --text "What title do you want to convert?")

HandBrakeCLI -i "$*" -t "${title}" -o /media/disk/"${name}".m4v -I -X 320

zenity --info --text "The DVD conversion is complete."

```

This code works for Zunes and iPods.

---

### Post by mssever on 2008-05-03
Glad you got it working. One comment, though: Using "$*" is probably not the best idea in this case. It combines all command line arguments into a single string. So if multiple files are selected, it'll probably fail. (I haven't tested this.) If you use "$1" you'll get just the first command line argument. "$2" for the second, etc. Alternately, you can use "$@" which is the same as "$*" except that each item is expanded to a separate double-quoted string. That means that you can make a loop and work through each file that may be selected.

---

