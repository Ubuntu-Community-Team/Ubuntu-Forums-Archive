---
title: "export tags from .flac to .mp3 using bash script"
date: 2007-05-04
forum: Programming Talk
---

### Post by mojoman on 2007-05-04
Hi all,

I looked for some lightweight soundconverters and the best that came up were ... bash scripts. Or pearl scripts but since I haven't done any programming since basic on my C64 some 25 years ago I'm gonna stick with bash for now (and having said that you can see that this is going to be at a laughable low level).

Now, I found quite a few scripts just by surfing around and some were quite useful but as the basic commands for converting audio formats are fairly easy even to me I figure this might be a good place to start learning bash scripts (I even bought a book in order to learn bash and I even went as far as to read it, however, I really need some practice). So, I made this one for starters:

```
for i in *.flac; do
flac -sdc "$i"  | lame -h -m s -b 256 - "${i%.flac}.mp3"
done
```

which simply converts all .flac files in the working directory to hifi mp3-files in stereo with a 256 bitrate, keeping the name (save for the extension).

But then I realised that I'm missing out on the tags here so I wanted to expand the script. I thought that exporting the tags from the .flac files (using metaflac) and then writing that to the .mp3 files (using id3) would be a good idea but I'm not sure how to go about this (or even if it's a good idea).

Could anyone give me some pointers ont this?

Thanks!

---

### Post by jamescox84 on 2007-05-09
I don't know if you got a solution to this in the end, but I liked the problem so I wrote a python script to do the job for you.

flactomp3:
```

#!/usr/bin/env python

import os
import os.path
import sys


LAME_BITRATE = 256


def escape_quotes(path):
    return path.replace('"', r'\"')


# Get's the tag of a flac file    
def get_flac_tag(flac_file, tag):
    flac_file = os.path.abspath(flac_file)
    
    # Mack sure the path existes and that the file exists
    if not os.path.exists(flac_file) or not os.path.isfile(flac_file):
        return ''
    
    flac_file = escape_quotes(flac_file)
    
    f = os.popen('metaflac --show-tag=%s "%s"' % (tag.upper(), flac_file))
    meta_out = f.read()
    f.close()
    
    try:
        return meta_out[meta_out.find('=') + 1:].strip()
    except:
        return ''
    

def encode_mp3(flac_file):
    mp3_file, ext = os.path.splitext(flac_file)
    wave_file = escape_quotes(mp3_file + '.wav')
    mp3_file = escape_quotes(mp3_file + '.mp3')
    flac_file = flac_file
    
    # Converts to wave
    os.system('flac -d -f "%s"' % escape_quotes(flac_file))
    
    year = get_flac_tag(flac_file, 'DATE')
    if year: year = year[:5]
    title = escape_quotes(get_flac_tag(flac_file, 'TITLE'))
    artist = escape_quotes(get_flac_tag(flac_file, 'ARTIST'))
    album = escape_quotes(get_flac_tag(flac_file, 'ALBUM'))
    track_number = int('0' + get_flac_tag(flac_file, 'TRACKNUMBER'))
    # Missing out GENRE because genre is stored a index in mp3 but as a string in flac
    
    command = 'lame -h -m s -b %d --tt "%s" --ta "%s" --tl "%s" --ty %s --tn %d "%s" "%s"' \
              % (LAME_BITRATE, title, artist, album, year, track_number, wave_file, mp3_file)
    
    # Conerts wave to mp3 then deletes wave
    os.system(command)
    os.system('rm "%s"' % wave_file)
    
    
if __name__ == '__main__':
    if len(sys.argv) != 2:
        print 'uage: flactomp3 <flacfile>'
        sys.exit(1)
        
    flac_file = sys.argv[1]
    
    if not os.path.exists(flac_file) or not os.path.isfile(flac_file):
        print '%s is not found.' % (flac_file)
        sys.exit(1)

    encode_mp3(flac_file)

```

It's a bit of a hack, but then most useful scripts are. Hope this helped!

---

### Post by mojoman on 2007-05-11
Cool. I'll try it out.

I'm still interested in trying to put something together in bash though, mainly to learn so if anyone has an idea of what to use (i.e. is the idea with metaflac and id3 worth pursuing) and tips on how to go about it I would be very interested.

Thanks
/mojoman

---

### Post by jamescox84 on 2007-05-11
I wish I could help you with bash, it's something I'd really want to get my head around. Very often things can be done in one line using I/O redirection. Less typing is always something I'm in favor of.

---

### Post by process91 on 2007-05-18
I found this at the [Linux Tutorial Blog]("http://www.linuxtutorialblog.com/post/solution-converting-flac-to-mp3") and I thought I would share it with you. It seems to be very similar to what you are trying to do, only that this is for one file. It should be really easy to change that though.

--------------------------------------------------
#!/bin/bash
FLAC=$1
MP3="${FLAC%.flac}.mp3"
[ -r "$FLAC" ] || { echo can not read file \"$FLAC\" >&1 ; exit 1 ; } ;
metaflac --export-tags-to=- "$FLAC" | sed 's/=\(.*\)/="\1"/' >tmp.tmp
cat tmp.tmp
. ./tmp.tmp
rm tmp.tmp
flac -dc "$FLAC" | lame -b 192 -h --tt "$Title" \
--tn "$Tracknumber" \
--tg "$Genre" \
--ty "$Date" \
--ta "$Artist" \
--tl "$Album" \
--add-id3v2 \
- "$MP3"
-------------- end of script ----------

---

### Post by foresth on 2007-05-19
Thanks jamescox84 and process91! I craved for this too :].

---

### Post by nighthwk1 on 2008-12-28
I know this thread is old, but I modified the python script to work with multiple flac files (you can do "flac2mp3 *.flac"):

```

#!/usr/bin/env python

import os
import os.path
import sys

LAME_QUALITY = 0

def escape_quotes(path):
	return path.replace('"', r'\"')


# Gets the tag of a flac file
def get_flac_tag(flac_file, tag):
	flac_file = os.path.abspath(flac_file)

	# Make sure the path exists and that the file exists
	if not os.path.exists(flac_file) or not os.path.isfile(flac_file):
		return ''

	flac_file = escape_quotes(flac_file)

	f = os.popen('metaflac --show-tag=%s "%s"' % (tag.upper(), flac_file))
	meta_out = f.read()
	f.close()

	try:
		return meta_out[meta_out.find('=') + 1:].strip()
	except:
		return ''


def encode_mp3(flac_file):
	mp3_file, ext = os.path.splitext(flac_file)
	wave_file = escape_quotes(mp3_file + '.wav')
	mp3_file = escape_quotes(mp3_file + '.mp3')
	flac_file = flac_file

	# Converts to wave
	os.system('flac -d -f "%s"' % escape_quotes(flac_file))

	year = get_flac_tag(flac_file, 'DATE')
	if year: year = year[:5]
	title = escape_quotes(get_flac_tag(flac_file, 'TITLE'))
	artist = escape_quotes(get_flac_tag(flac_file, 'ARTIST'))
	album = escape_quotes(get_flac_tag(flac_file, 'ALBUM'))
	track_number = int('0' + get_flac_tag(flac_file, 'TRACKNUMBER'))
	# Missing out GENRE because genre is stored a index in mp3 but as a string in flac

	command = 'lame -h -V %d --tt "%s" --ta "%s" --tl "%s" --ty %s --tn %d "%s" "%s"' \
	% (LAME_QUALITY, title, artist, album, year, track_number, wave_file, mp3_file)

	# Converts wave to mp3 then deletes wave
	os.system(command)
	os.system('rm "%s"' % wave_file)


def main(argv):
	for i in argv:
		flac_file = i

		if not os.path.exists(flac_file) or not os.path.isfile(flac_file):
			print '%s is not found.' % (flac_file)
			sys.exit(1)

		encode_mp3(flac_file)


if __name__ == '__main__':
	if len(sys.argv) < 2:
		print 'usage: %s <flacfile(s)>' % (sys.argv[0])
		sys.exit(1)
		
	main(sys.argv[1:])

```

---

### Post by eric.frederich on 2009-05-28
Came accross this thread because I needed something too.

Process91.

The bash script you posted wouldn't be that easy to put in a loop.
It winds up setting environment variables for each tag which which may or may not exist in the next file to be processed.  You could possibly write a 2nd script which calls your 1st script.  Anyway, it used pipes and inspired me to improve the python version to do the same.  Actually more or a re-write to suit my taste.

New features:


[LIST=1]
[*]Externalized the lame switch to metaflac tag mapping so new supported switches can be added easily.  I noticed the --tc and --tg switches in the lame man page.  I don't know the equivalent metaflac tag names for them hence the question marks.
[*]No temporary files, use pipes instead.  This should improve performance.
[*]Only calling metaflac once per file and getting the entire set of tags as a dictionary.  This should also improve performance.
[*]Possible bug fix.  Quotes were not the only things that needed escaping.  Using subprocess.Popen removes the need to do any of escaping.
[/LIST]

```
#!/usr/bin/env python

import os
import sys
import re
from subprocess import Popen, PIPE

lame_switches = ['--preset', 'standard']

tag_re = re.compile('(?P<tag>[^=]*)=(?P<value>.*)')

lame_to_metaflac_mapping = {
    '--tt': 'TITLE'      ,
    '--ta': 'ARTIST'     ,
    '--tl': 'ALBUM'      ,
    '--ty': 'DATE'       ,
    '--tn': 'TRACKNUMBER',
    '--tc': '??COMMENT??',
    '--tg': '??GENRE??'  ,
}

def get_tags(flac_file):
    ''' Returns flac tags as a python dictionary
    '''
    p = Popen(['metaflac', '--export-tags-to', '-', flac_file], stdout=PIPE)
    out, err = p.communicate()
    return dict([tag_re.match(line).groups() for line in out.splitlines()])

def tags_to_lame_switches(tags):
    ''' Converts tags to a list of lame switches based on lame_to_metaflac_mapping.
    '''
    switches = []
    for switch, tag in lame_to_metaflac_mapping.items():
        if tag in tags:
            switches.append(switch)
            switches.append(tags[tag])
    return switches

def flac_to_mp3(flac_file):
    ''' Creates a .mp3 file with the same file name as the .flac file.
        Preserves meta data.
    '''
    tags = get_tags(flac_file)
    tag_switches = tags_to_lame_switches(tags)
    base_name, ext = os.path.splitext(flac_file)
    mp3_file = '%s.mp3' % base_name
    
    # s, d, c == silent, decode, stdout
    p1 = Popen(['flac', '-sdc', flac_file], stdout=PIPE, stderr=PIPE)
    p2 = Popen(['lame'] + lame_switches + tag_switches + ['-', mp3_file], stdin=p1.stdout, stdout=PIPE, stderr=PIPE)
    p2.communicate()
    
def main(flac_files):
    for flac_file in flac_files:
        if not os.path.isfile(flac_file):
            print '%s is not found.  Skipping.' % (flac_file,)
            continue
        print flac_file
        flac_to_mp3(flac_file)

if __name__ == '__main__':
    if len(sys.argv) < 2:
        print 'usage: %s <flacfile(s)>' % (sys.argv[0],)
        sys.exit(1)
    main(sys.argv[1:])

```

Note: Untested on Ubuntu.  Gentoo user here ;)

---

### Post by rpkehoe on 2009-06-07
Necroposting I know...but I ran into the same thing and did it bash with a little error checking for anyone who is interested.

```
#!/bin/bash
# Will convert every flac file in the current directory to mp3's using the highest 
# possibly quality setting of the lame encoder.  flac should support passing multiple
# files via wildcard, but I have found it to not be trustworthy, plus a loop is needed for
# lame anyways.  Intermediate wav's are deleted.
# 6/6/2009

# Use the lame encoder preset
preset=insane

# Find the number of flac files in lower case
lcflac_cnt=`ls | grep -c .flac`

# Find all the flac files
allflac_cnt=`ls | grep -c -i .flac`

# Exit if there are upper case flac's
if [ $lcflac_cnt != $allflac_cnt ]; then
  echo "There are some flac's with upper case extensions."
  echo "I didn't feel like accounting for them, please fix them and run the script again."
  exit
fi

# Exit if there are no files to process
if [ $lcflac_cnt = 0 ]; then
  echo "Hey, there isn't anything to do...that was quick."
  exit
fi

# Initialize the tag variables so lame won't bomb if they don't exist
tt=""
ta=""
tt=""
ty=""
tc=""
tn=""
tg=""

# Actually do some work
for flac in `ls *.flac`; do
  echo "running flac"
  flac -d $flac
  base=${flac%.flac}
  echo "Export metatags"
  metaflac $flac --export-tags-to=${base}.tag
  tt=`grep -i title ${base}.tag | cut -f 2 -d \=`
  ta=`grep -i artist ${base}.tag | cut -f 2 -d \=`
  tl=`grep -i album ${base}.tag | cut -f 2 -d \=`
  # Some people use album, some use venue.
  tl_cnt=`echo $tl | wc -c`
  if [ "$tl_cnt" -lt "2" ]; then
    tl=`grep -i venue ${base}.tag | cut -f 2 -d \=`
  fi
  ty=`grep -i "date" ${base}.tag | cut -f 2 -d \=`
  tc=`grep -i comment ${base}.tag | cut -f 2 -d \=`
  tn=`grep -i track ${base}.tag | cut -f 2 -d \=`
  tg=`grep -i genre ${base}.tag | cut -f 2 -d \=`
  echo "time for lame"
  lame --preset $preset \
       --tt "$tt" \
       --ta "$ta" \
       --tl "$tl" \
       --ty "$ty" \
       --tc "$tc" \
       --tn "$tn" \
       --tg "$tg" \
       --add-id3v2 \
       ${base}.wav ${base}.mp3
  echo "remove wav's"
  rm ${base}.wav
  echo "remove tag file"
  rm ${base}.tag
done

# See if everything was processed
mp3_cnt=`ls *.mp3 | wc -l`
if [ $mp3_cnt != $lcflac_cnt ]; then
  echo "There are $lcflac_cnt flacs and $mp3_cnt mp3's, you should check into that."
fi
```

---

