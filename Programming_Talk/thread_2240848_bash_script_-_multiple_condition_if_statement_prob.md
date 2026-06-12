---
title: "bash script - multiple condition if statement problem"
date: 2014-08-22
forum: Programming Talk
---

### Post by getut2 on 2014-08-22
I'm stuck on yet another scripting problem.

I have files in a folder named DailyDetail<date> and WeeklyDetail<date>. I have a variable that gets assigned the relative file path to those files ($activefile and another that is "base" name of the file ($1) provided as a parameter.

If the file is the weekly variant I need to do some error checking to make sure the file is populated to the minimum valid file size. I'm not having any luck.

I've tried lots of variations of the below but the main help I have found on the internet lists && and -a as the two ways of doing multiple condition ifs. These are the only 2 variants that don't immediately throw an error, but they don't actually seem to trigger if the file is less than 24510 bytes either.  I know each of the 2 components are correct because they each run correctly when only 1 at a time is tested for.

I've tried this:
```
        if [[ $1 = "WeeklyDetail" && `wc -c $activefile | cut -f 1 -d ' '` < 24510 ]]; then
            echo "File is $1 and it is too damn small"
        else
            echo "if condition for $1 didn't run properly"
        fi
```

and
```
        if [ $1 = "WeeklyDetail" && `wc -c $activefile | cut -f 1 -d ' '` < 24510 ]; then
            echo "File is $1 and it is too damn small"
        else
            echo "if condition for $1 didn't run properly"
        fi
```

---

### Post by steeldriver on 2014-08-22
I think the issue is that it's doing a lexical (string) comparison

```

$ if [[ true && 11111 < 2345 ]]; then echo "less than"; else echo "not less than"; fi
less than

```

To do a numeric comparison, use (( )) or -lt

```

$ if [[ true ]] && (( 11111 < 2345 )); then echo "less than"; else echo "not less than"; fi
not less than

$ if [ true -a 11111 -lt 2345 ]; then echo "less than"; else echo "not less than"; fi
not less than

```

EDIT: btw have you considered using

```

stat -c '%s' file

```

for the size in bytes (instead of wc + cut)?

---

### Post by ofnuts on 2014-08-24
> **steeldriver said:**
> 

EDIT: btw have you considered using

```

stat -c '%s' file

```

for the size in bytes (instead of wc + cut)?

+1 to that, avoids reading the file... 

I'm also wondering if the logic couldn't be changed using a 'find' to list only the files above/below the threshold size.

---

### Post by steeldriver on 2014-08-24
... although I got my knuckles rapped for suggesting the same over on U&L because the %s format specifier is a GNU extension (i.e. not POSIX compliant) apparently

I can't really justify it, but stylistically if it was me I'd probably be thinking about a case statement for the filename test, with a simple size test inside that i.e. something like

```

case "$1" in
  "somefile") 
    (( "$(stat -c '%s' "$1")" < 100 )) && echo "too small" || echo "just right"
    ;;
    
  "otherfile")
    echo "do something with $1"
    ;;
   
  *)
    echo "not a file I know about"
    ;;
esac

```

As you say, depending on context a 'find -name "somefile" -size +12345' might work better

---

### Post by Vaphell on 2014-08-24
POSIX compliance is overrated. If i was paid top dollar for admining some ancient, obscure unix i'd care but i don't so i don't. Life's too short for strict POSIX compliance ;-)

---

### Post by ofnuts on 2014-08-24
> **Vaphell said:**
> POSIX compliance is overrated. If i was paid top dollar for admining some ancient, obscure unix i'd care but i don't so i don't. Life's too short for strict POSIX compliance ;-)

After the grammar nazis, the Posix nazis :) 

Back to stat, it appears that the BSD stat indeed uses different format specifiers. But then bash may have its built-in implementation of stat, so things get complicated. 

OTOH real Posix scripts are written for sh, not bash, so as soon as you use Bash the Posix argument loses a lot of its validity.

PS: personally I have more problems with ancient Linux... I sometimes have to write scripts that run on a 2010 RedHat, which appears to have frozen its source in 2005. And the 2005 coreutils are missing many things compared to those of my 2012 Kubuntu.

---

### Post by Vaphell on 2014-08-24
damn, RedHat sure loves 'stability'. 9 years of progress, bugfixes and goodies. Which version of bash would that be? I'd like to know what features i would miss

---

### Post by ofnuts on 2014-08-25
I'm away from work so cannot check actual versions. IIRC Bash is mostly OK, it's the "coreutils" that are missing useful stuff, like, from memory, the '--executable' flag in find, or the %m format specifier in stat. So the scripts I write on my PC don't always work on the servers...

---

