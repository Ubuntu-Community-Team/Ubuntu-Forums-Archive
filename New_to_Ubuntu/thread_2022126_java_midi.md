---
title: "java midi"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by eubulide on 2012-07-10
Hi everyone,
  I am reading a book called "Head First Java" by Kathy Sierra and Bert Bates. One example piece of code uses a MIDI sequencer to generate a sound.
Unfortunately it doesn't work for me on Ubuntu. When I run it I only hear a kind of knock (it's supposed to be a piano note). I don't know anything about sound and MIDI devices, so I don't know how to fix the problem.

I give the code below.
After compiling it I execute the command with different arguments:
java MiniMusicCmdLine 102 30
java MiniMusicCmdLine 80 20
java MiniMusicCmdLine 40 70

They're supposed to produce notes of different pitch, but I always hear the same short knock.

I welcome any help at the beginner level.

-----------------------

import javax.sound.midi.*;

public class MiniMiniMusicCmdLine {

    public static void main(String[] args) {
    MiniMiniMusicCmdLine mini = new MiniMiniMusicCmdLine();
    if (args.length < 2) {
        System.out.println("Don't forget the instrument and note args");
    } else {
        int instrument = Integer.parseInt(args[0]);
        int note = Integer.parseInt(args[1]);
        mini.play(instrument,note);
    }
    } // close main

    public void play(int instrument, int note) {
    try {
        Sequencer player = MidiSystem.getSequencer();
        player.open();
        Sequence seq = new Sequence(Sequence.PPQ, 4);
        Track track = seq.createTrack();

        MidiEvent event = null;

        ShortMessage first = new ShortMessage();
        first.setMessage(192, 1, instrument, 0);
        MidiEvent changeInstrument = new MidiEvent(first, 1);
        track.add(changeInstrument);

        ShortMessage a = new ShortMessage();
        a.setMessage(144, 1, note, 100);
        MidiEvent noteOn = new MidiEvent(a, 1);
        track.add(noteOn);

        ShortMessage b = new ShortMessage();
        a.setMessage(128, 1, note, 100);
        MidiEvent noteOff = new MidiEvent(b, 16);
        track.add(noteOff);

        player.setSequence(seq);
        player.start();
    } catch (Exception ex) {ex.printStackTrace();}
    } // close play

} // close class

---

