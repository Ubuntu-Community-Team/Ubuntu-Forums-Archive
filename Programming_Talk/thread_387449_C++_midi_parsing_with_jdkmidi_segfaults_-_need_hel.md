---
title: "C++ midi parsing with jdkmidi segfaults - need help debugging"
date: 2007-03-18
forum: Programming Talk
---

### Post by simplyw00x on 2007-03-18
As part of my light-speed re-acquaintance with C++ for my project [Guitarshik]("http://moho.frihost.net/covertninja/?p=102"), I need to parse midi, which is a serious headache. The best midi library I've found with the right features is jdkmidi, but I'm having problems using it as a sequencer to parse the file and call functions per note.

```
void PlayDumpSequencer( MIDISequencer *seq )
{	
  float pretend_clock_time = 0.0;
  float next_event_time = 0.0;
  MIDITimedBigMessage *ev;
  int ev_track;
  
  seq->GoToTimeMs( pretend_clock_time );
  
  if( !seq->GetNextEventTimeMs( &next_event_time ) )
  {
    return;
  }
  
  // simulate a clock going forward with 10ms resolution for 1 minute
  // cout << pretend_clock_time << ":" << next_event_time << "\n";
  for( ; pretend_clock_time<60.0*1000.0; pretend_clock_time+=10.0 )
  {
    cout << "position 1: " << pretend_clock_time << ":" << next_event_time << "\n";
    // find all events that came before or a the current time
    while( next_event_time <= pretend_clock_time )
    {
        cout << "position 2 \n";
      if( seq->GetNextEvent( &ev_track, ev ) )
      {
        cout << "position 3 \n";
        // found the event!
        // show it to stdout
        
        //fprintf( stdout, "tm=%06.0f : evtm=%06.0f :trk%02d : ", pretend_clock_time, next_event_time, ev_track );

        cout << "position 4 \n";
        
        // DumpMIDITimedBigMessage( ev );
        
        // now find the next message

        if( !seq->GetNextEventTimeMs( &next_event_time ) )
        {
          // no events left so end
          
          fprintf( stdout, "End\n" );
          return;
        }

        cout << "position 6 \n";
        
      }			
    }		
  }
}
```

This is taken almost verbatim from the example (which also crashes), and the debugging 'cout << "position...."' statements tell me that the call to GetNextEvent crashes as soon as pretend_clock_time is greater than 0. This is an odd problem, but I can't really see how to proceed in fixing.

Does anyone have any ideas?

---

### Post by Wybiral on 2007-03-18
The midi file format is pretty straightforward, you might consider parsing it yourself if you can't find a worthy library.

This page has some good spec's:
[http://www.sonicspot.com/guide/midifiles.html](http://www.sonicspot.com/guide/midifiles.html)

---

### Post by j_g on 2007-03-18
MIDI File Format is not the same thing as MIDI.

For information about MIDI, you can look at my own MIDI webpage at [http://users.adelphia.net/~jgglatt](http://users.adelphia.net/~jgglatt)

---

### Post by Wybiral on 2007-03-18
The signals are basically the same whether it's streaming from a device or read from a file.

---

### Post by j_g on 2007-03-19
> The signals are basically the same whether it's streaming from a device or read from a file.

Why do some people on this board think that they have to be an authority on _absolutely everything_ including stuff that they obviously have no practical programming experience with?

Um no. MIDI File Format is not MIDI. That's why there are two entirely different specifications for them from the MMA. Indeed, MIDI File Format didn't even appear until 3 years after the MIDI Specification. (You can read about the two, in excruciating detail, on my web site). The former is simply a sequencer file format meant to store MIDI data with time stamping and other information pertinent to sequencer software (but which may not have any particular bearing upon MIDI itself, and in fact, is not transferred at all over a MIDI connection). MIDI is realtime I/O. The difference would be akin to a text file versus two people conversing.

I don't know the details of the particular MIDI tool he's using, but it's apparent from the function names that he's trying to do MIDI playback (ie, I/O). I don't know if this tool is loading data from MIDI File Format, or merely playing back recorded data in its own internal format, generating data on-the-fly, or what. It can't be determined from the snippet. But it doesn't matter. It's obvious that this tool is supposed to be managing all the low level loading/retrieving/whatever of data, as well as playback. Just telling him to jettison this tool, without giving him any specific, equivalent options, suggesting that his problem has to do with loading a MIDI File Format (when that isn't even identified as the problem -- I would think the author of the tool would have tested that this very basic feature, if supported, works), is not at all helpful advice.

Now, as I said, I have never looked at jdkmidi, but I have written my own MIDI File Format save/load library, and MIDI I/O, so I'll take a guess at what's going on based upon some working knowledge of this type of thing.

The original poster says that he is getting a crash at

```

if( seq->GetNextEvent( &ev_track, ev ) )

```

From the function name, I'm guessing that this fetches the address of the next "MIDI event" (within several tracks of data), as well as the track number containing this event. I'm guessing the MIDI data is stored in a MIDITimedBigMessage (whatever that is), and since the address of this MIDITimedBigMessage is returned, then he needs to pass a handle as so:

```

if( seq->GetNextEvent( &ev_track, &ev ) )

```

If this is the case, then the crash he's getting is because he's not passing the address of where he wants the pointer (to a MIDITimedBigMessage) stored. He's passing the current value of his ev variable (which is garbage because it hasn't been initialized yet. That's why I've made this educated guess as to what's going wrong. Why would a function be passed garbage? Christ, did you not even _look_ at his code before you "helpfully" told him to just throw it away and find something else??? Even if you know next to nothing about MIDI, anyone with a passing knowledge of C++ should have spotted this very suspicious, inexplicable coding).

In conclusion, I'm guessing he either made a mistake transcribing the example, or he got it from some documentation where the author made that mistake. He probably needs to pass a handle to GetNextEvent.

---

### Post by Wybiral on 2007-03-19
> **j_g said:**
> Why do some people on this board think that they have to be an authority on _absolutely everything_ including stuff that they obviously have no practical programming experience with?

Um no. MIDI File Format is not MIDI. That's why there are two entirely different specifications for them from the MMA. Indeed, MIDI File Format didn't even appear until 3 years after the MIDI Specification. (You can read about the two, in excruciating detail, on my web site). The former is simply a sequencer file format meant to store MIDI data with time stamping and other information pertinent to sequencer software (but which may not have any particular bearing upon MIDI itself, and in fact, is not transferred at all over a MIDI connection). MIDI is realtime I/O. The difference would be akin to a text file versus two people conversing.

I don't know the details of the particular MIDI tool he's using, but it's apparent from the function names that he's trying to do MIDI playback (ie, I/O). I don't know if this tool is loading data from MIDI File Format, or merely playing back recorded data in its own internal format, generating data on-the-fly, or what. It can't be determined from the snippet. But it doesn't matter. It's obvious that this tool is supposed to be managing all the low level loading/retrieving/whatever of data, as well as playback. Just telling him to jettison this tool, without giving him any specific, equivalent options, suggesting that his problem has to do with loading a MIDI File Format (when that isn't even identified as the problem -- I would think the author of the tool would have tested that this very basic feature, if supported, works), is not at all helpful advice.

Now, as I said, I have never looked at jdkmidi, but I have written my own MIDI File Format save/load library, and MIDI I/O, so I'll take a guess at what's going on based upon some working knowledge of this type of thing.

The original poster says that he is getting a crash at

```

if( seq->GetNextEvent( &ev_track, ev ) )

```

From the function name, I'm guessing that this fetches the address of the next "MIDI event" (within several tracks of data), as well as the track number containing this event. I'm guessing the MIDI data is stored in a MIDITimedBigMessage (whatever that is), and since the address of this MIDITimedBigMessage is returned, then he needs to pass a handle as so:

```

if( seq->GetNextEvent( &ev_track, &ev ) )

```

If this is the case, then the crash he's getting is because he's not passing the address of where he wants the pointer (to a MIDITimedBigMessage) stored. He's passing the current value of his ev variable (which is garbage because it hasn't been initialized yet. That's why I've made this educated guess as to what's going wrong. Why would a function be passed garbage? Christ, did you not even _look_ at his code before you "helpfully" told him to just throw it away and find something else??? Even if you know next to nothing about MIDI, anyone with a passing knowledge of C++ should have spotted this very suspicious, inexplicable coding).

In conclusion, I'm guessing he either made a mistake transcribing the example, or he got it from some documentation where the author made that mistake. He probably needs to pass a handle to GetNextEvent.

j_g... You need to _calm_ down.

What I meant (calm down) was that the messages that are encoded in midi files are basically the same messages received from a device. At least in all of the midi files (stay calm) I've seen.

I was just stating that the midi messages were essentially the same.

Actually, I never ""helpfully" told" him/her not to use the (calm down) library they are using, I said "if you can't find a worthy library". I admit, I was wrong to assume they were asking about reading midi files (that's what I've been working on lately, it was on my mind).

I just don't see why you're getting so upset because about things... CALM DOWN.

---

### Post by simplyw00x on 2007-03-19
j_d is correct in that what I'm trying to do here is read a Midi file, however I'm not trying to play it: what I'm trying to do is sequence through it (obeying tempo instructions), generating an event every time the parser hits a note. I now realise this process seems a lot like playing the file.....

```
if( seq->GetNextEvent( &ev_track, &ev ) )
```

I'll try that. Thanks.

---

### Post by WW on 2007-03-19
That change won't work unless you also change this
```
MIDITimedBigMessage *ev;
```
to this
```
MIDITimedBigMessage ev;
```

---

### Post by j_g on 2007-03-19
Right. Just surfed over to the jdkmidi page, and the docs show that GetNextEvent wants a pointer, not a handle. So as noted by WW, you have to change your definition of your ev variable. It should be an instance of a MIDITimedBigMessage. And pass the address of it it to GetNextEvent:

```

MIDITimedBigMessage ev;

...

if( seq->GetNextEvent( &ev_track, &ev ) )

...

```

---

### Post by simplyw00x on 2007-03-20
This has possibly been the most tedious thing ever; having tried (I kid you not) 4 o 5 midi classes from Koders.org, all with their own little idiosyncrasies, I returned to jdkmidi after seeing some replies to this thread. The help you guys gave encouraged me to have another try, this time doing lots of
```
std::cout << "Position 1 \n";
```
in the libray function itself. I finally found a useless block of code that crashes inexplicably when pretend_clock_time > next_event_time, commented it out, and now everything is working (touch wood...).

Thanks for everyone's help. Greatly appreciated.

---

### Post by FoxMulder900@yahoo.com on 2008-04-15
Hello, 
     I know this post is about a year old, but I too am trying to use jdkmidi  . I am having no problems parsing midi files, but I was wondering if anyone has successfully used jdkmidi to actually play a midi file. If not if anyone knows of a library that I could use to create tracks and play them on the fly, that would be very helpful! Thanks in advance!

---

### Post by koftinoff on 2008-06-14
Hey guys, I'm the author of libjdkmidi and just saw this thread.  It is probably best to email me directly if you have any problems with it as I don't normally read all the threads on ubuntuforums.

Anyways, there have been some bug fixes to the library. The latest version is always on SVN at 

[http://opensource.jdkoftinoff.com/jdks/svn/trunk/libjdkmidi/trunk/](http://opensource.jdkoftinoff.com/jdks/svn/trunk/libjdkmidi/trunk/)

My wiki has more information on it:

[http://opensource.jdkoftinoff.com/jdks/trac/wiki/libjdkmidi](http://opensource.jdkoftinoff.com/jdks/trac/wiki/libjdkmidi)

So do the following from the command line to get it:

```
svn co http://opensource.jdkoftinoff.com/jdks/svn/trunk/libjdkmidi/trunk/ libjdkmidi
```

There were some bugs in earlier versions, and even this latest version does not have some features complete, such as the EditTrack for editing midi tracks, that I had implemented for other closed source projects.

When I have more time I'd love to upgrade the library to be more 'modern c++' style using STL/boostism/software transaction memory etc. But in the meantime a lot of people do use the current library for currently shipping products, both open and closed source.  

Yes, I can dual license the library under GPLv2 and other if we make a deal.

Regards,
Jeff Koftinoff
[www.jdkoftinoff.com](www.jdkoftinoff.com)

---

