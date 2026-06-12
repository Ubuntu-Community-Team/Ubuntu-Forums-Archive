---
title: "midi library"
date: 2008-09-29
forum: Programming Talk
---

### Post by lapubell on 2008-09-29
I've been reading about the alsa midi api, and want some opinions, and maybe some suggestions.

I have been googling for some information on using python (or any other language) to capture midi events.  Most of the stuff I find is about reading and writing midi files, which is good and all, but I was looking for more information about how to caputre midi events.

All the articles seem to point back to [http://www.mxm.dk/products/public/pythonmidi/](http://www.mxm.dk/products/public/pythonmidi/), which is awesome in and of itself, but this all seems to work with midi files, input and output and whatnot.

What I really want is to be able to plug in my midi device, hit a key and see the midi channel, note, and all that other midi output in a terminal.  I can take it from there.

It doesn't even need to be python.  Anything?

This is much appreciated!

---

### Post by PC-XT on 2008-10-03
I found this link helpful for the Windows C++ way:
[http://209.85.165.104/search?q=cache:_zQRtrFzeM4J:www.experts-exchange.com/Programming/Misc/Q_20630822.html+midi+capture+java&hl=en&ct=clnk&cd=8&gl=us&client=firefox-a](http://209.85.165.104/search?q=cache:_zQRtrFzeM4J:www.experts-exchange.com/Programming/Misc/Q_20630822.html+midi+capture+java&hl=en&ct=clnk&cd=8&gl=us&client=firefox-a)

For Java, the input port is found by iterating over all the items returned by MidiSystem.getMidiDeviceInfo. Here is source for a program that lists both input and output midi devices: from [http://lists.apple.com/archives/Java-dev/2007/Oct/msg00350.html](http://lists.apple.com/archives/Java-dev/2007/Oct/msg00350.html)```
import javax.sound.midi.*;

public class ListMidiDevices {
	public static void main(String[] args) {
		for (MidiDevice.Info info : MidiSystem.getMidiDeviceInfo()) {
			try {
				MidiDevice device = MidiSystem.getMidiDevice(info);
				boolean bAllowsInput = (device.getMaxTransmitters() != 0);
				boolean bAllowsOutput = (device.getMaxReceivers() != 0);
				System.out.println((bAllowsInput ? "IN " : "   ")
						+ (bAllowsOutput ? "OUT " : "    ") + info.getName()
						+ ", " + info.getDescription());
			} catch (MidiUnavailableException mue) {
				mue.printStackTrace();
			}
		}
		System.exit(0);
	}
}
```Once you have a port, I think you can read MIDI events from the transmitter returned by getTransmitter or something.

---

