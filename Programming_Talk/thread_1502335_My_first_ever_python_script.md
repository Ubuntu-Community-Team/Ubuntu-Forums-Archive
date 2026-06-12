---
title: "My first ever python script"
date: 2010-06-05
forum: Programming Talk
---

### Post by kempy1000 on 2010-06-05
Hi

I have been attempting to learn python in order to get away from using bash so much!

As a project script I wanted to be able to tweet when my mythtv setup starts recording and what it is recording.

There are scripts that do this but they also tweet everytime I started watching livetv as it is technically a recording.

So after much reading and two hours of working I have this:

```

#!/usr/bin/python

##################################################################################
# A script to check the recording status of the mythbackend
# Ignores livetv only reports recordings.
#
# Chris Kemp 2010 - kempy1000@gmail.com
##################################################################################

import httplib
import time
import MythTV
import twitter
import re
from MythTV import MythDB, MythBE

####################################
#START VARIABLES
####################################

#This is what is shown in the tweet before the show name
prefix = 'Recording: '

#Twitter api login
api = twitter.Api(username='#############', password='#########')

#Mythtv database connection
db1 = MythDB(args=(('DBHostName','localhost'),
                  ('DBName','mythconverg'),
                  ('DBUserName','mythtv'),
                  ('DBPassword','########')))

#This is what the script looks for on the mythbackend status page in mythweb to determine if a recording is in progress
Encoder1 = "Encoder 1 "
Encoder2 = "Encoder 2 "
Recording = "is local on chimera and is recording"

####################################
#END VARIABLES
####################################

#Initalize variables to prevent repetative tweeting
LastTweet1 = ' '
LastTweet2 = ' '

#Mythtv backend using the given database parameters
be1 = MythBE(db=db1)

#Start the loop
while(True):
        #The backend address with the myth status port
        Connection = httplib.HTTPConnection("localhost:6544")
        Connection.request("GET", "/")
        Results = Connection.getresponse().read()

        if Encoder1+Recording in Results:
                #Get the recording name using the mythtv python bindings
                REC1 = be1.getCurrentRecording(1)
                #Truncate all the rubbish from the returned string to get human readable format
                tempstr = str(REC1)[10:]
                Show = tempstr[:-37]
                #Check if the show being recorded has already been tweeted
                if LastTweet1 != Show:
                        #if not tweet it and mark it as tweeted
                        LastTweet1 = Show
                        tempPrefix = prefix
                        tempPrefix += Show
                        #Tweet
                        api.PostUpdate(tempPrefix)

        if Encoder2+Recording in Results:
                #Get the recording name using the mythtv python bindings
                REC2 = be1.getCurrentRecording(2)
                #Truncate all the rubbish from the returned string to get human readable format
                tempstr = str(REC2)[10:]
                Show = tempstr[:-37]
                #Check if the show being recorded has already been tweeted
                if LastTweet2 != Show:
                        #if not tweet it and mark it as tweeted
                        LastTweet2 = Show
                        tempPrefix = prefix
                        tempPrefix += Show
                        #Tweet
                        api.PostUpdate(tempPrefix)

        #Sleep then reloop do not set this too low! (~60 minimum)
        time.sleep(120)

```

Posting incase anyone else wants to use it.

Also looking for any advice on improvement to the code or programming standards as I doubt very much that it is 100 percent efficient and perfectly written! :)

Thanks
Chris

---

### Post by StephenF on 2010-06-05
Firstly, well done on producing something useful.

If I'm going to criticise anything it's the copy/paste/modify programming style that will get you into trouble when writing larger programs. Using an Encoder class it's possible to rewrite this program to scale to any number of encoders you like and any program modifications would only need to be done in one place rather than repeated over and over.

Classes are covered in the python tutorial.

---

### Post by kempy1000 on 2010-06-05
Thank you very much for the advice I wouldnt have had a clue how to improve this script!

After looking into what you said ive come up with this:
```

#!/usr/bin/python

##################################################################################
# A script to check the recording status of the mythbackend
# Ignores livetv only reports recordings.
#
# Chris Kemp 2010 - kempy1000@gmail.com
##################################################################################

import httplib
import time
import MythTV
import twitter
import re
from MythTV import MythDB, MythBE

####################################
#START VARIABLES
####################################

#This is what is shown in the tweet before the show name
prefix = 'Recording: '

#Twitter api login
api = twitter.Api(username='########', password='########')

#Mythtv database connection
db1 = MythDB(args=(('DBHostName','localhost'),
                  ('DBName','mythconverg'),
                  ('DBUserName','mythtv'),
                  ('DBPassword','########')))


#This is what the script looks for on the mythbackend status page in mythweb to determine if a recording is in progress
Recording = "is local on chimera and is recording"
Encoder = [' ', 'Encoder 1 ', 'Encoder 2 ']

####################################
#END VARIABLES
####################################

#Mythtv backend using the given database parameters
be1 = MythBE(db=db1)
#Storage for last tweets to prevent retweeting
LastTweet = [' ', 'Nothing', 'Nothing']

def EncoderCheck( Numb ):
        if Encoder[Numb]+Recording in Results:
                #Get the recording name using the mythtv python bindings
                REC = be1.getCurrentRecording(Numb)
                #Truncate all the rubbish from the returned string to get human readable format
                tempstr = str(REC)[10:]
                Show = tempstr[:-37]
                #Check if the show being recorded has already been tweeted
                if LastTweet[Numb] != Show:
                        #if not tweet it and mark it as tweeted
                        LastTweet[Numb] = Show
                        tempPrefix = prefix
                        tempPrefix += Show
                        #Tweet
                        api.PostUpdate(tempPrefix)

#Start the loop
while(True):
        #The backend address with the myth status port
        Connection = httplib.HTTPConnection("localhost:6544")
        Connection.request("GET", "/")
        Results = Connection.getresponse().read()

        EncoderCheck(1)
        EncoderCheck(2)

        #Sleep then reloop do not set this too low! (~60 minimum)
        time.sleep(120)

```

Its a smaller file and I presume more efficient, and I understand what you mean about the copy paste code now and realise why a this is a better solution!

Thanks
Chris

---

### Post by StephenF on 2010-06-05
Okay, here is my effort which demonstrates how a class could be used. I have not run this (I don't have MythTV, so there will likely be bugs) but I think I got the gist of your code.
```

import httplib
import twitter
import time
from MythTV import MythDB, MythBE


class Encoder(object):
    """Class to analyse MythTV encoder activity."""

    def is_recording(self, mythdata):
        return self.match in mythdata
        
    def current_recording(self, mythdata):
        """Returns whatever the encoder is currently recording."""

        if self.is_recording(mythdata):
            return str(self.back_end.getCurrentRecording(self.id))[10:-37]
        else:
            return None

    def new_recording(self, mythdata):
        """Returns None for all but new recordings."""

        rec = self.current_recording(mythdata):
        if rec == self.old_rec:
            return None
        else:
            self.old_rec = rec
            return rec
    
    def __init__(self, back_end, id):
        self.back_end = back_end
        self.id = id
        self.match = 'Encoder %d is local on chimera and is recording' % id
        self.old_rec = None
        

def main():
    # Connect to Twitter and MythTV backend.
    twitter_h = twitter.Api(username='########', password='########')
    myth_be = MythBE(db=MythDB(args=(('DBHostName','localhost'),
         ('DBName','mythconverg'), ('DBUserName','mythtv'),
         ('DBPassword','########'))))

    # Make a list of Encoder objects for encoders 1 and 2. 
    encoders = [Encoder(myth_be, x) for x in xrange(1, 3)]
    
    while 1:
        # Obtain MythTV status info.
        conn = httplib.HTTPConnection('localhost:6544')
        conn.request('GET', '/')
        mythdata = conn.getresponse().read()

        # Check each encoder in turn.
        for enc in encoders:
            show = enc.new_recording(mythdata)
            if show is not None:
                twitter_h.PostUpdate('Recording: %s' % show)

       time.sleep(120)


if __name__ == '__main__':
    main()

```

---

### Post by kempy1000 on 2010-06-06
That works perfectly with a tiny modification

Change:
```

    def new_recording(self, mythdata):
        """Returns None for all but new recordings."""

        rec = self.current_recording(mythdata):
        if rec == self.old_rec:
            return None
        else:
            self.old_rec = rec
            return rec

```
To:
```

    def new_recording(self, mythdata):
        """Returns None for all but new recordings."""

        rec = self.current_recording(mythdata)
        if rec == self.old_rec:
            return None
        else:
            self.old_rec = rec
            return rec

```

Thank you for the help, im reading into python quite a lot now!

---

### Post by kempy1000 on 2010-06-06
Just a final question on this script!

I am trying to get the script so it is generic and not fixed for my machine.

The only change I need now is this line:
```

self.match = 'Encoder %d is local on chimera and is recording' % id

```
I changed it to:
```

self.match = 'Encoder %d is local on %s and is recording' % (id,behostname)

```
and used 
```

behostname = os.uname()[1]

```
to get the hostname and it works all except for some reason I noticed the tweets get the last char cut from them?

Eg:
```

Recording: The Simpson

```
Should be:
```

Recording: The Simpsons

```

How has my minor change done this?
Thanks
Chris

---

### Post by kempy1000 on 2010-06-06
Just an error couldnt reproduce.

Thank you very much for the help.

Chris

---

