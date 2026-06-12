---
title: "Python multi-threaded audio"
date: 2010-06-09
forum: Programming Talk
---

### Post by djbushido on 2010-06-09
So i'm trying to get multiple audio streams playing at the same time, such as a DJ might use. I am currently using pygame to try and get a high-level access to the audio. However, when I try and multi-thread pygame, I can't get two music streams to play. What happens is that when I execute the playback code in a separate thread, playback just restarts. The launcher code:```
import pyDJ_Audio
import threading
import time

class pyDJ_Deck(threading.Thread):
        def __init__(self, filename=None):
                threading.Thread.__init__(self)
                self.filename = filename
        def run(self):
                pyDJ_Audio.sound_file_load('/home/bra[CODE]
```d/Music/Begun.ogg')
                pyDJ_Audio.sound_start_playback()


def deckStart():
        pyDJ_Audio.sound_file_load('/home/brad/Music/Begun.ogg')
        pyDJ_Audio.sound_start_playback()

pyDJ_Audio.sound_init()
Deck1 = pyDJ_Deck()
Deck1.start()
time.sleep(5)
Deck2 = pyDJ_Deck()
Deck2.start()
time.sleep(10)
[/CODE]
and the backend code:```
import pygame.mixer as mixer
music_player = mixer.music

def sound_init(frequency=44100, size=-16, channels=2, buffer=8192):
        mixer.init(frequency, size, channels, buffer)
        mixer_settings = mixer.get_init()
        if mixer_settings == None:
                print("Mixer not initialized correctly")
        else:
                mixer_initialized = True
                print("Mixer initialized to:")
                print("Frequency: " + str(mixer_settings[0]))
                print("Sample Size: " + str(mixer_settings[1]))
                print("Channels: " + str(mixer_settings[2]))

def sound_file_load(filename):
        music_player.load(filename)
        sound_loaded = True

def sound_start_playback(start_pos = 0.0):
        music_player.play(start_pos)


```
So far as I know, pygame uses SDL for the backend.
Is there a good way to do this, or do I have to write a C++ library and have two references to that? Or is there a totally better way and I really need to learn audio programming?

EDIT: Did another test, works as expected when I use two processes - is there a way to attempt this in a single process.

---

### Post by djbushido on 2010-06-09
Ok, so I figured it out. You have to maintain 2 channel objects, which each hold a Sound file for the track you want to play. Annoying, but can technically avoid threading.

---

