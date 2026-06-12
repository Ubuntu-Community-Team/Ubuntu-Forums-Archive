---
title: "extract song title from a .cue file"
date: 2010-08-23
forum: Programming Talk
---

### Post by miak on 2010-08-23
Hi,

I am trying to create couple of cd's and for that I downloaded some .flac recordings, but they are not split so I decided to write a script to do spliting, naming and taging of the songs. I found that splitting is easy and there are already software to do that(cuetools & shnsplit), but I have trouble naming newly splitted songs.
I tried going through contents of .cue file using awk, but it seems that awk processes each line separately, so there is no way to get the title of the song if you have track number, or is there?
Basecally my problem is: given multi-line input(.cue file), how can I extract title of a specific song?
Here is an example .cue file
```
REM GENRE Rock 
REM DATE 2002 
REM DISCID 28122C14 
REM COMMENT "ExactAudioCopy v0.99pb4" 
PERFORMER "The Rolling Stones" 
TITLE "Forty Licks (CD 1)" 
FILE "Rolling Stones - Forty Licks (CD 1).flac" WAVE 
  TRACK 01 AUDIO 
    TITLE "Street Fighting Man" 
    PERFORMER "The Rolling Stones" 
    INDEX 01 00:00:00 
  TRACK 02 AUDIO 
    TITLE "Gimme Shelter" 
    PERFORMER "The Rolling Stones" 
    INDEX 00 03:14:70 
    INDEX 01 03:16:45
.......
.......
```

Thanks,
miak

---

### Post by surfer on 2010-08-23
i wrote something in python some time ago... it's not exactly what you need, but easy enough to adapt (i hope...)

```

#!/usr/bin/python
# -*- coding: utf-8 -*-


'''


'''


import os.path
# import shutil
import re
import sys



class CueTrackData(object):
    '''
    cue data for one track
    '''
    
    def __init__(self,
                 track_number = None, 
                 index_number = None, 
                 index_time   = None,
                 title        = None,
                 performer    = None):

        self.track_number = track_number
        self.index_number = index_number
        self.index_time   = index_time

        self.title        = title
        self.performer    = performer
        
    
    def __str__(self):
        ret = ''

        ret += "track_number = '%s'\n" % self.track_number
        ret += "index_number = '%s'\n" % self.index_number
        ret += "index_time   = '%s'\n" % self.index_time
        if self.title is not None:
            ret += "title        = '%s'\n" % self.title
        if self.performer is not None:
            ret += "performer    = '%s'\n" % self.performer
       
        return ret

   

class CueData(object):
    '''
    Parse the CueTrackData for all tracks in a cue sheet.
    '''

    CUE_FILE_RE_STR = r'''
                       (?P<file>FILE)                # the FILE statement
                       (?P<whitespace0>\s)           # whitespace
                       (?P<opening>\")               # "
                       (?P<wav_filename>.*\.flac)    # the filename of the flac
                       (?P<closing>\")               # "
                       (?P<whitespace1>\s)           # whitespace
                       '''
                       # FILE "dummy.wav" WAVE

    CUE_FILE_RE = re.compile(CUE_FILE_RE_STR, re.VERBOSE)



    INDEX_RE_STR = r'''(?P<const_track>TRACK)               # the TRACK statement
                       (?P<whitespace0>\s*)                 # whitespace  
                       (?P<track_number>\d{2})              # track number
                       (?P<whitespace1>\s*)                 # whitespace  
                       (?P<const_audio>AUDIO)               # the AUDIO statement
                       (?P<whitespace2>\s*)                 # whitespace
                       (?P<const_title>TITLE)               # the TITLE statement
                       (?P<whitespace3>\s*)                 # whitespace
                       (?P<opening1>\")                     # "
                       (?P<title>.*)                        # the title
                       (?P<closing1>\")                     # "
                       (?P<whitespace4>\s*)                 # whitespace 
                       (?P<const_performer>PERFORMER)       # the AUDIO statement
                       (?P<whitespace5>\s*)                 # whitespace 
                       (?P<opening2>\")                     # "
                       (?P<performer>.*)                    # the title
                       (?P<closing2>\")                     # "
                       (?P<whitespace6>\s*)                 # whitespace 
                       (?P<const_index>INDEX)               # the INDEX statement       
                       (?P<whitespace7>\s*)                 # whitespace  
                       (?P<index_number>\d{2})              # index number
                       (?P<whitespace8>\s*)                 # whitespace 
                       (?P<index_time>\d{2}:\d{2}:\d{2})    # index time
                       '''
    INDEX_RE = re.compile(INDEX_RE_STR, re.VERBOSE)

    def __init__(self, cue_str):

        self.cue_str = cue_str
        self.wav_filename = None
        self.tracks = []

    def parse(self):


        res = CueData.CUE_FILE_RE.search(self.cue_str)
        self.wav_filename = res.group('wav_filename')

        res = CueData.INDEX_RE.finditer(self.cue_str)
        for item in res:

            data = CueTrackData(
                    title        = item.group('title'),
                    performer    = item.group('performer'),
                    track_number = item.group('track_number'), 
                    index_number = item.group('index_number'), 
                    index_time   = item.group('index_time')
                    )
            self.tracks.append(data)


    def merge_fileData(self, fileData):
        for (fle, cue) in zip(fileData.tracks,self.tracks):

            cue.title = fle.title
            cue.performer = fileData.artist.decode('utf-8')

  

    def __str__(self):
        ret = ''

        # ret += "cue_path = '%s'\n" % self.cue_str
        ret += "wav_filename = '%s'\n" % self.wav_filename
        for track in self.tracks:
            ret += '%s\n' % str(track)

        return ret


if __name__ == '__main__':


    def test(argv):
        cue_str = '''
REM GENRE Rock 
REM DATE 2002 
REM DISCID 28122C14 
REM COMMENT "ExactAudioCopy v0.99pb4" 
PERFORMER "The Rolling Stones" 
TITLE "Forty Licks (CD 1)" 
FILE "Rolling Stones - Forty Licks (CD 1).flac" WAVE 
  TRACK 01 AUDIO 
    TITLE "Street Fighting Man" 
    PERFORMER "The Rolling Stones" 
    INDEX 01 00:00:00 
  TRACK 02 AUDIO 
    TITLE "Gimme Shelter" 
    PERFORMER "The Rolling Stones" 
    INDEX 00 03:14:70 
    INDEX 01 03:16:45

'''

        cd = CueData(cue_str)
        cd.parse()
        print cd


    def main(argv):
        pass

    #import sys
    # main(sys.argv)
    test([sys.argv[0]])


```

---

### Post by DaithiF on 2010-08-23
Hi, if the title line always follows track number line, then a 1-liner in sed would be:
```
sed -n "/TRACK 0\?${id} /{N;s/^[^\"]*\"\(.*\)\"\s*$/\1/;p}" cuefile
```
where id contains the track number

---

### Post by ghostdog74 on 2010-08-23
awk is perfectly suitable for parsing files. I don't know what kind of output you want since you did not show examples.

```

$ awk '/TRACK/{printf "%s",$2;getline;$1="";gsub(/\042/,"");gsub(/ +/,".");print}' file
01.Street.Fighting.Man
02.Gimme.Shelter


```

---

### Post by miak on 2010-08-23
Thanks for quick replies.

ghostdog74's example is the closest what I want, it actually extracts all the info I need, but in a slightly different format.
my script is going to rename songs from "xx.flac" to "xx. title.flac", and I think I'll do, but now I'm really curious what exactly does the awk line do. To be precise the beginning /TRACK/, and getline in the middle. 
If you can explain that it would be perfect.

Best,
miak

---

### Post by ghostdog74 on 2010-08-23
it says look for lines with pattern TRACK, get the track id number and print it. "getline" read in the next line, then the title will be the 2nd column onwards. gsub() removes all double quotes, and changes spaces to dots. Please read the gawk manual (in my sig) to know about awk.

---

### Post by StephenF on 2010-08-23
Some code I spent way too much time writing.
```

class CueSheet(object):
   """A class for parsing cue sheets."""

   _operands = (("PERFORMER", "SONGWRITER", "TITLE", "PREGAP", "POSTGAP"),
                ("FILE", "TRACK", "INDEX"))
   _operands = dict((k, v + 1) for v, o in enumerate(_operands) for k in o)

   # Try to split a string into three parts with a large quoted section
   # and parts fore and aft.
   _quoted = re.compile(r'(.*?)[ \t]"(.*)"[ \t](.*)').match

   def _time_handler(self, time_str):
      """Returns the number of frames of audio (75ths of seconds)

      Minutes can exceed 99 going beyond the cue sheet standard.

      """
      try:
         mm, ss, ff = [int(x) for x in time_str.split(":")]
      except ValueError:
         raise ValueError("time must be in (m*)mm:ss:ff format %s" % self.line)

      if ff < 0 or ff > 74 or ss < 0 or ss > 59 or mm < 0:
         raise ValueError("a time value is out of range %s" % self.line)

      return ff + 75 * ss + 75 * 60 * mm

   def _int_handler(self, int_str):
      """Attempt to convert to an integer."""

      try:
         ret = int(int_str)
      except:
         raise ValueError("expected integer value for %s %s", (int_str, self.line))
      return ret

   @classmethod
   def _tokenize(cls, iterable):
      """Scanner/tokenizer for cue sheets.
      
      This routine will iteratively take one line at a time and return
      the line number, command, and any operands related to the command.
      
      Quoted text will have spaces and tabs intact and counts as one,
      otherwise all consecutive non-whitespace is a token. The first
      token is the command, the rest are it's operands.
      
      """
      for i, line in enumerate(iterable):
         line = line.strip() + " "
         match = cls._quoted(line)
         if match:
            left, quoted, right = match.groups()
            left = left.replace("\t", " ").split()
            right = right.replace("\t", " ").split()
         else:
            left = line.replace("\t", " ").split()
            right = [""]
            quoted = ""
               
         tokens = filter(lambda x: x, left + [quoted] + right)
         yield i + 1, tokens[0].upper(), tokens[1:]

   def _parse_PERFORMER(self):
      self.segment[self.tracknum][self.command].append(self.operand[0])
      
   _parse_SONGWRITER = _parse_TITLE = _parse_PERFORMER

   def _parse_FILE(self):
      if not self.operand[1] in ("WAVE", "MP3", "AIFF"):
         raise ValueError("unsupported file type %s" % self.line)
         
      self.filename = self.operand[0]
      self.prevframes = 0
      
   def _parse_TRACK(self):
      if self.filename is None:
         raise ValueError("no filename yet specified %s" % self.line)

      if self.tracknum and self.index < 1:
         raise ValueError("track %02d lacks a 01 index" % self.tracknum)

      if self.operand[1] != "AUDIO":
         raise ValueError("only AUDIO track datatype supported %s" % self.line)

      num = self._int_handler(self.operand[0])
      self.tracknum += 1
      self.index = -1
      if num != self.tracknum:
         raise ValueError("unexpected track number %s" % self.line)
                  
   def _parse_PREGAP(self):
      if self.tracknum == 0 or self.index != -1 or "PREGAP" in self.segment[self.tracknum]:
         raise ValueError("unexpected PREGAP command %s" % self.line)
         
      self.segment[self.tracknum]["PREGAP"] = self._time_handler(self.operand[0])

   def _parse_INDEX(self):
      if self.tracknum == 0:
         raise ValueError("no track yet specified %s" % self.line)
      
      if "POSTGAP" in self.segment[self.tracknum]:
         raise ValueError("INDEX command following POSTGAP %s" % self.line)
      
      num = self._int_handler(self.operand[0])
      frames = self._time_handler(self.operand[1])
      
      if self.tracknum == 1 and self.index == -1 and frames != 0:
         raise ValueError("first index must be zero for a file %s" % self.line)

      if self.index == -1 and num == 1:
         self.index += 1
      self.index += 1
      if num != self.index:
         raise ValueError("unexpected index number %s" % self.line)
         
      if frames < self.prevframes:
         raise ValueError("index time before the previous index %s" % self.line)
         
      if self.prevframes and frames == self.prevframes:
         raise ValueError("index time no different than previously %s" % self.line)
         
      self.segment[self.tracknum][self.index] = (self.filename, frames)
      
      self.prevframes = frames
                  
   def _parse_POSTGAP(self):
      if self.tracknum == 0 or self.index < 1 or "POSTGAP" in self.segment[self.tracknum]:
         raise ValueError("unexpected POSTGAP command %s" % self.line)
         
      self.segment[self.tracknum]["POSTGAP"] = self._time_handler(operand[0])

   def parse(self, iterable):
      """Return a parsed cuesheet object."""
      
      self.filename = None
      self.tracknum = 0
      self.segment = defaultdict(partial(defaultdict, list))

      for self.i, self.command, self.operand in self._tokenize(iterable):
         if self.command not in self._operands:
            continue

         self.line = "on line %d" % self.i

         if len(self.operand) != self._operands[self.command]:
            raise ValueError("wrong number of operands got %d required %d %s" %
                  (len(self.operand), self._operands[self.command], self.line))
         else:
            getattr(self, "_parse_" + self.command)()

      if self.tracknum == 0:
         raise ValueError("no tracks")
         
      if self.index < 1:
         raise ValueError("track %02d lacks a 01 index" % tracknum)
       
      for each in self.segment.itervalues():
          del each.default_factory
      del self.segment.default_factory
                 
      return self.segment

```
Usage
```

with open(cue_pathname) as f:
   segment_data = CueSheet().parse(f)

```
That will create a dictionary of tracks with dictionaries within for the index. Generally...

# Pull filename and offset tuple for track 1 index 1.
segment_data[1][1]

# Get the performer and title of track 1.
segment_data[1]["PERFORMER"]
segment_data[1]["TITLE"]

---

### Post by scarfaceDeb on 2010-09-06
can you post the function 'defaultdict' too.
cause i'm getting errors about:

self.segment = defaultdict(partial(defaultdict, list))

there's no defaultdict function in code.

thanks a lot.

i've been trying to understand your code and refabricate it to my script, but it's my first serious program and i found it hard to understand some things, especially not mine.

---

### Post by scarfaceDeb on 2010-09-06
ok, i've found where you got those functions. 
sometimes i forgot about google, sorry)

---

