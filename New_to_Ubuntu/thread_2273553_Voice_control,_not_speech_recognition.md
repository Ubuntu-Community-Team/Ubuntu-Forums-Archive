---
title: "Voice control, not speech recognition"
date: 2015-04-14
forum: New to Ubuntu
---

### Post by Kevin McCready on 2015-04-14
I know voice control relies on speech recognition, but I just want to issue basic commands by voice such as page up, down, alt-tab, enter, next etc.

I understand voice control is software to send operational commands to a computer. Speech recognition or voice recognition is software to distinguish thousands of words in human language. I want voice control and I would prefer it installed on my computer (not having to run off to the internet each time I say 'page down').

I tried Simon but it wasn't user friendly for me.

I don't know how to configure Sphinx or Julius to help me.

Any solutions would be welcome.

For the record, and to help others perhaps, here's my research:
CMU Sphinx, also called Sphinx in short, is the general term to describe a group of speech recognition systems developed at Carnegie Mellon University. These include a series of speech recognizers (Sphinx 2 - 4) and an acoustic model trainer (SphinxTrain).  Pocketsphinx is a library that depends on another library called SphinxBase which provides common functionality across all CMUSphinx project
/
Julius is a high-performance, two-pass large vocabulary continuous speech recognition (LVCSR) decoder software for speech-related researchers and developers.
/
Kaldi a toolkit for speech recogntion provided under the Apache licence.
/

    Speech[1] uses Google's speech recognition engine to support dictation in many different languages.
    Speech Control: is a Qt-based application that uses CMU Sphinx's tools like SphinxTrain and PocketSphinx to provide speech recognition utilities like desktop control, dictation and transcribing to the Linux desktop.
    Platypus[2] is an open source shim that will allow the proprietary Dragon NaturallySpeaking running under Wine to work with any Linux X11 application.
    FreeSpeech,[3] from the developer of Platypus, is a free and open source cross-platform desktop application for GTK that uses CMU Sphinx's tools to provide voice dictation, language learning, and editing in the style of Dragon NaturallySpeaking.
    Vedics (Voice Enabled Desktop Interaction and Control System) is a speech assistant for GNOME Environment
    Xvoice[5] (requires proprietary ViaVoice to function)
    GnomeVoiceControl[6] is a dialogue system to control the GNOME Desktop that was developed in the Google Summer of Code in 2007.
    NatI is a multi-language voice control system written in Python
    CVoiceControl[8] is a KDE and X Window independent version of its predecessor KVoiceControl
    SphinxKeys[9] lets you essentially type keyboard keys and mouse clicks by speaking into your microphone. It's simple and works pretty much out of the box.
    Open Mind Speech,[10] a part of the Open Mind Initiative,[11] aims to develop free (GPL) speech recognition tools and applications, as well as collect speech data.
    PerlBox[12] is a perl based control and speech output.
    VoxForge is a free speech corpus and acoustic model repository for open source speech recognition engines.
    Simon[13] aims at being extremely flexible to compensate dialects or even speech impairments. It uses either HTK / Julius or CMU SPHINX, works on Windows and Linux and supports training.
    Speeral Speeral a group of speech recognition tools developed at University of Avignon

Simon is an open-source speech recognition program and replaces the mouse and keyboard. It is in development for physically disabled people and seniors

---

### Post by Kevin McCready on 2015-04-19
bump

---

### Post by paradj on 2015-11-02
me too...
 BUMP!

No one has any opinions or recommends for this?

---

### Post by grahammechanical on 2015-11-02
There are two projects that are not exactly what you a looking for but they show the direction that certain ideas are moving in

[http://sirius.clarity-lab.org/](http://sirius.clarity-lab.org/)

[https://insights.ubuntu.com/2015/08/14/meet-mycroft-open-source-artificial-intelligence-powered-by-snappy/](https://insights.ubuntu.com/2015/08/14/meet-mycroft-open-source-artificial-intelligence-powered-by-snappy/)

The Ubuntu Online Summit has a show & tell session by the Mycroft people on what they are achieving. The session will be held on 15.00 UTC on 5th November. This is this Thursday.

They are plans, also to be discussed the summit for a Ubuntu desktop version built on Snappy Ubuntu Core which will no doubt have the Mycroft software (snaps) in the app store.

[http://summit.ubuntu.com/uos-1511/2015-11-05/](http://summit.ubuntu.com/uos-1511/2015-11-05/)

Regards.

---

