---
title: "Which is better? [p. language]"
date: 2008-11-26
forum: Programming Talk
---

### Post by debuti on 2008-11-26
Hello everyone

I mean, i use to code bash scripts all the time to automate tasks, but has reached a moment where it is likely that people that i know needs them, and the problem is that they do not use linux (or bash).
Well, my idea is to keep writing these scripts in a more portable scripting language, such as perl or python, but I do not like to lose usual bash/unix commands/utilities as find, grep, sort, awk, diff, du, date, etc. and if its posibble id like to be able to use some common apis like gdata or flickr's.

What scripting language do you recommend me for this? 
Should I stay in coding bash?
With what language could you achieve faster developing and more portability?

Thanks for the reading :)

P.D.
 Example useful script that i coded
[INDENT][INDENT]
#!/bin/bash
################################################################################
#  Author: Borja Garcia <debuti@gmail.com>
# Program: getFullPath.sh
# Descrip: Returns the full path of the given file (standalone function to 
#          include in your own scripts)
# Version: 0.0.0
#    Date: 2008-11-14:18:47:00
# License: This script doesn't require any license since it's not intended to be
#          redistributed.
#          In such case, unless stated otherwise, the purpose of the author is
#          to follow GPLv3.
# Version: 0.0.0 (2008-11-14:18:47:00)
#           - Initial release
################################################################################

# Usage function

  function usage() {
    # Tell the user how to use me
    echo "usage: $0 <valid file to get the full path>"
  }
  
# Input validation function (getopts)

  function checkInput() {
    if [ $# -ne 1 ]; then
      usage $0
      exit -1
    fi
  }

# Helper functions
  
  function getFullPath() {
      file=""
      actual=`pwd`
      output=""
      temp=""

    if [ -e "$1" ]; then
      file="$1"
    else
      return -1
    fi

    if [ `echo $file | cut -c1,1` = "/" ]; then
      output=$file
    else
      output="$actual"/"$file"
      output=`echo $output | sed -e "s/\/\.\//\//g"`                          #Ignore /./
      while [ `echo $output | grep "/../"` ]; do
        output=`echo $output | sed -e "s/\/[^\/^(\.\.)]*\/\.\.\//\//g"`       #Delete /somewhere/../
        output=`echo $output | sed -e "s/^\/\.\.\//\//g"`
      done
      output=`echo $output | sed -e "s/\/\//\//g"`                            #Ignore //

    fi

    if [ -e "$output" ]; then
      echo "$output"
    else
      echo "Can't do it :S $output" 1>&2
      return -2
    fi
  }
  
# Main function

  function main() {
    getFullPath "$1"
  }

# Entry point
  checkInput $@
  main $@[/INDENT][/INDENT]

---

### Post by MicahCarrick on 2008-11-26
"Which is better?" is probably not a good question to ask as one or another may not be "better". Each has their advantages and disadvantages and you'll find it comes down to a multitude of factors, largely personal preference and experience.

That being said, I think you will like Python--especially if you'll want them to work for you on linux as well as your friends on Windows. I'm a recent convert to Python when it suits my needs. The reason I will throw my opinion towards Python (and remember, it's just an opinion) is because it has so many features available to replace and/or use grep, awk, etc. But at the same time, you will still have those tools when running in Linux. Additionally, learning Python is very quick and developing in Python is very quick compared to some of the others.

I would NOT keep writing bash scripts if you even intend for them to run on Windows and other platforms (though you can do so using things such as MinGW or Cygwin). You bash skills will still serve you well in other languages.

---

### Post by ZuLuuuuuu on 2008-11-26
> **debuti said:**
> ... but I do not like to lose usual bash/unix commands/utilities as find, grep, sort, awk, diff, du, date, etc. and if its posibble id like to be able to use some common apis like gdata or flickr's.


This sounds more like a Perl situation here. Usually Perl is more suitable for people coming from shell scripting -and who wants to keep the shell scripting feel-. It even has some functions borrowed from shell scripting, awk etc... And for API's, there are thousands of modules in [Perl CPAN]("http://www.cpan.org"). CPAN is the module archive for Perl. For example, gdata search brings:

[http://search.cpan.org/search?query=gdata&mode=all](http://search.cpan.org/search?query=gdata&mode=all)

and Flickr search brings:

[http://search.cpan.org/search?query=flickr&mode=all](http://search.cpan.org/search?query=flickr&mode=all)

I'm sure Python have this kind of modules, too, but Python is for you if you want to learn a completely new programming language. Its syntax is even different than C family (Not completely different, though).

I like Python's syntax very much but it is different while Perl's is alike.

---

### Post by nvteighen on 2008-11-26
Perl is more used as shell-scripting language than Python, but I just wouldn't discard it as a possibility. What you'll surely get from both is some independence from the GNU utilities by using built-in language features.

---

### Post by Cracauer on 2008-11-26
Sorry, but the original question is screwed up.

The reason why you can't easily use sh or bash script on Windoze is that these commands are missing. That situation won't change when you use perl or python to call these commands.

---

### Post by Sorivenul on 2008-11-27
I'm personally a Python person, however, looking at your example, Perl may suit you better.

My advice, check out both, try a few simple scripts beyond the traditional "Hello, World!", and choose from there.  
[pmasiar's Wiki]("http://learnpython.pbwiki.com/HowToStart") has some great information on Python.
[Picking up Perl]("http://www.ebb.org/PickingUpPerl/") is a freely redistributable Perl tutorial, and the one I used to begin with.  Others may offer different routes.

Good luck!

---

