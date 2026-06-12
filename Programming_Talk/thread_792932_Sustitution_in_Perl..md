---
title: "Sustitution in Perl."
date: 2008-05-13
forum: Programming Talk
---

### Post by ibuclaw on 2008-05-13
Hi all.

Quick question:
How do I substitute strings while printing them in perl? (ie: **WITHOUT** _appending_ the _change_ to the string).

ie:
BASH Example
```

export rhyme="baabaablacksheep"          # assign string to variable.
printf "%s\n" "$rhyme"                   # print string.
printf "%s\n" "${rhyme##baabaa}"         # remove baabaa from string.
printf "%s\n" "${rhyme/baabaa/foobar}"   # replace baabaa with foobar.
printf "%s\n" "${rhyme//b/k}"            # replace all matches of b with k.
printf "%s\n" "$rhyme"                   # print string again.

```

Will produce the output:
[PHP]
baabaablacksheep
blacksheep
foobarblacksheep
kaakaaklacksheep
baabaablacksheep
[/PHP]
Without altering the original string.

Any help would be appreciated.

Regards
Iain

---

### Post by ibuclaw on 2008-05-13
Or, shall I say; more specifically.

The cutting of an unknown path of a string (and the cutting of all but the suffix), so just the basename is left over, but leaving the string intact so it can be used later:

Some more BASH...
For this example, lets presume:
$1 = /path/to/foobar.suffix
$Info = /path/to/info/folder
$Files = /path/to/files/folder
```

if [ "${1##*.}" == "suffix" ]; then
#SOME CODE.
printf "%s\n" "[Info]" > "$Info/${1##/*/}.info"
printf "%s\n" "Path=$Path" >> "$Info/${1##/*/}.info"
printf "%s\n" "Date=$Date" >> "$Info/${1##/*/}.info"
#SOME MORE CODE.
mkdir -p "$Files/${1##*.}"
mv "$1" "$Files/${1##*.}/${1##/*/}"
fi

```
Notice the use of $1.

[EDIT]
Yes, I'm converting one of my BASH scripts to Perl, for those who will read this and say "That is not Perl!".

I'm switching because of the speed increase of using Perl and the apparent superior use of string manipulation...
And, I don't really know Perl very well. But I'm learning by example as I successfully convert each of my scripts, section by section into the language.
So far, all I've hit is this huge stump that's preventing me from continuing...

Regards
Iain

---

### Post by slavik on 2008-05-13
there is the substitute operator ...

$string = "Hello world";
$string =~ s/Hello//g;

would get rid of Hello.

---

### Post by ibuclaw on 2008-05-13
> **slavik said:**
> there is the substitute operator ...

$string = "Hello world";
$string =~ s/Hello//g;

would get rid of Hello.

Yes, I realise, and removing it is exactly the opposite of what I wanted to do...

On the upside I've found "fileparse()", which will just about do.

BASH:
```

printf "%s\n" "[Info]" > "$Info/${1##/*/}.info"

```
Perl Equivalent:
[PHP]
use File::Basename;
open INFOFILE, ">$Info/" . fileparse($ARGV[0]) . ".info";
print INFOFILE "[Info]";
[/PHP]

Now I'm just looking through for one that will strip out all but the suffix.

Thanks anyway.

Regards
Iain

---

