---
title: "Beginner programming challenge #4"
date: 2009-05-11
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2009-05-11
I come up with an idea quicker than I expected. So here is the new programming challenge, have fun!

[SIZE="4"][FONT="Arial"][COLOR="Purple"]**Short Description**[/COLOR][/FONT][/SIZE]

In this programming challenge we are going to take the first steps for creating an mp3/ogg player. Our mp3 player won't play music, actually, but it will pretend that it is playing a playlist.

[SIZE="4"][FONT="Arial"][COLOR="Purple"]**How It Should Work**[/COLOR][/FONT][/SIZE]

There is a text file named my_songs.txt (given below) which includes the information about the mp3s we have, in a format like this:

```
ARTIST NAME | ALBUM NAME | SONG NAME
ARTIST NAME | ALBUM NAME | SONG NAME
ARTIST NAME | ALBUM NAME | SONG NAME
ARTIST NAME | ALBUM NAME | SONG NAME
.
.
.
```

Our software is supposed to read this file, hold the song information in its memory in a proper way and then wait for our commands.

Commands we can give to the software will include:

**play**: When this command is given, our software will start playing the current song and notify us like: "Now playing: SONG NAME - ARTIST NAME".

**pause**: When this command is given, our software will notify us like: "Paused".

**next**: When this command is given, our software will start playing the next song on the playlist and notify us like again: "Now playing: SONG NAME - ARTIST NAME". Note that it should play the next song on the same album if it is not the last song on the album.

[SIZE="4"][FONT="Arial"][COLOR="Purple"]**my_songs.txt**[/COLOR][/FONT][/SIZE]

```
MxPx | Secret Weapon | 01 - Secret Weapon
MxPx | Secret Weapon | 02 - Shut It Down
MxPx | Secret Weapon | 03 - Here's To The Life
MxPx | Secret Weapon | 04 - Top Of The Charts
MxPx | Secret Weapon | 05 - Punk Rawk Celebrity
MxPx | Secret Weapon | 06 - Contention
Nirvana | Bleach | 01 - Blew
Nirvana | Bleach | 02 - Floyd The Barber
Nirvana | Bleach | 03 - About A Girl
Nirvana | Bleach | 04 - School
Nirvana | Nevermind | 01 - Smells Like Teen Spirit
Nirvana | Nevermind | 02 - In Bloom
Nirvana | Nevermind | 03 - Come As You Are
Nirvana | Nevermind | 04 - Breed
Nirvana | Nevermind | 05 - Lithium
Nirvana | In Utero | 01 - Serve The Servants
Nirvana | In Utero | 02 - Scentless Apprentice
Nirvana | In Utero | 03 - Heart-Shaped Box
Nirvana | In Utero | 04 - Rape Me
Nirvana | In Utero | 05 - Frances Farmer Will Have Her Revenge On Seattle
Papa Roach | Metamorphosis | 01 - Days Of War
Papa Roach | Metamorphosis | 02 - Change Or Die
Papa Roach | Metamorphosis | 03 - Hollywood *****
Papa Roach | Metamorphosis | 04 - I Almost Told You That I Loved You
Papa Roach | Metamorphosis | 05 - Lifeline
Papa Roach | Metamorphosis | 06 - Had Enough
Papa Roach | Metamorphosis | 07 - Live This Down
Papa Roach | Metamorphosis | 08 - March Out Of The Darkness
Queen | A Night At The Opera | 01 - Death On Two Legs
Queen | A Night At The Opera | 02 - Lazing On A Sunday Afternoon
Queen | A Night At The Opera | 03 - I'm In Love With My Car
Queen | A Night At The Opera | 04 - You're My Best Friend
Queen | A Night At The Opera | 05 - '39
Queen | A Night At The Opera | 06 - Sweet Lady
Queen | News Of The World | 01 - We Will Rock You
Queen | News Of The World | 02 - We Are The Champions
Queen | News Of The World | 03 - Sheer Heart Attack
Queen | News Of The World | 04 - All Dead, All Dead
Queen | News Of The World | 05 - Spread Your Wings
Queen | News Of The World | 06 - Fight From The Inside
Red Jumpsuit Apparatus | Don't You Fake It | 01 - In Fate's Hands
Red Jumpsuit Apparatus | Don't You Fake It | 02 - Waiting
Red Jumpsuit Apparatus | Don't You Fake It | 03 - False Pretense
Red Jumpsuit Apparatus | Don't You Fake It | 04 - Face Down
Red Jumpsuit Apparatus | Don't You Fake It | 05 - Misery Loves Its Company
Red Jumpsuit Apparatus | Don't You Fake It | 06 - Cat And Mouse
Rise Against | The Unraveling | 01 - Alive And Well
Rise Against | The Unraveling | 02 - My Life Inside Your Heart
Rise Against | The Unraveling | 03 - Great Awakening
Rise Against | The Unraveling | 04 - Six Ways 'Til Sunday
Rise Against | The Unraveling | 05 - 401 Kill
Rise Against | The Unraveling | 06 - The Art Of Losing
Rise Against | The Unraveling | 07 - Remains Of Summer Memories
Rise Against | The Unraveling | 08 - The Unraveling
Rise Against | The Unraveling | 09 - Reception Fades
Rise Against | The Unraveling | 10 - Stained Glass And Marble
Sepultura | Chaos A.D | 01 - Refuse - Resist
Sepultura | Chaos A.D | 02 - Territory
Sepultura | Chaos A.D | 03 - Slave New World
Sepultura | Chaos A.D | 04 - Amen
Sepultura | Chaos A.D | 05 - Kaiowas
Sepultura | Chaos A.D | 06 - Propaganda
Sepultura | Chaos A.D | 07 - Biotech Is Godzilla
```

[SIZE="4"][FONT="Arial"][COLOR="Purple"]**Extra Points**[/COLOR][/FONT][/SIZE]

Extra points will be given when you implement extra commands. To give some example ideas:

**shuffle**: After this command is executed a notification like "Shuffle mode: on" should be displayed and upcoming songs should be selected randomly from the list. When the command is executed again a notification like "Shuffle mode: off" should be displayed and upcoming songs should be played, in order again.

**repeat**: When this command is executed a notification like "Repeat: on" should be displayed and then the command "next" should always play the current song. If the command is executed again a notification like "Repeat: off" should be displayed and the player should play the songs normally, again.

You aren't tied to these ideas, you can implement any functionality for your own mp3 player and get extra points!

Another idea to get extra points: The list in my_songs.txt is already sorted in ASCII order but you can arrange your program so that it sorts the playlist in ASCII order even when the my_songs.txt is shuffled.

[SIZE="4"][FONT="Arial"][COLOR="Purple"]**Tricks**[/COLOR][/FONT][/SIZE]

Careful, there are more than 1 albums for some artists, they should be grouped in a proper way. Programmers who use high level languages can take advantage of hash data structures. Other language users can use arrays and structures.

[SIZE="4"][FONT="Arial"][COLOR="Purple"]**Finally**[/COLOR][/FONT][/SIZE]

Upcoming 3 weeks are final exam weeks for me so I will be able to check your solutions 3 weeks after. So you have 3 weeks :) (If this is too long, tell me and I'll think of a solution.)

Please specify how to compile/run your program if it is not written in a regular language like C/C++/Perl/Python/Ruby/Tcl.

---

### Post by gmatt on 2009-05-11
Is this really a test of how well you know your STL containers in C++ if you use C++, or your Java.util containers if you use Java, etc. ?

---

### Post by Bodsda on 2009-05-11
erm... I'l give this a go, I think I could manage it, but i definitely cant do all of the extra credit bits. 

Remember this is a 'beginner' programming challenge not an intermediate or medium skill programming challenge.

---

### Post by ZuLuuuuuu on 2009-05-11
All you have to know is basic things like to read a file, splitting a string, creating arrays and structs and getting input from user. The remaining part is if statements and printing text. No need for STL kind of stuff (actually I don't even know C++ but in C you don't need any additional library). Maybe you think like that because I said linked list but I said it for Lisp users :) (I don't know Lisp actually but I heard that everything is a list there)

...BUT... if a few more people complain then I'll come up with a simpler idea in 24 hours ;)

---

### Post by hessiess on 2009-05-11
> 
I don't know Lisp actually but I heard that everything is a list there


Nope, not everything is a list. Lisp, at least common lisp has hash tables and vectors too:)

---

### Post by wsonar on 2009-05-11
This one looks neat

So there are multiple BPC's  [http://ubuntuforums.org/showpost.php?p=5499486&postcount=1]("http://ubuntuforums.org/showpost.php?p=5499486&postcount=1") ?

---

### Post by Bodsda on 2009-05-11
> **wsonar said:**
> This one looks neat

So there are multiple BPC's  [http://ubuntuforums.org/showpost.php?p=5499486&postcount=1]("http://ubuntuforums.org/showpost.php?p=5499486&postcount=1") ?

I started these challenges to revive those ones you linked, LaRoZa did an excellent job of the previous beginner programming challenges, and when I saw people posting non-beginner challenges I decided to revive the old ones

---

### Post by Froodolt on 2009-05-12
Am I  the first to contribute?
Very nice challenge assignment, did learn much of it!

You got me Zuluuuuuuuuuuu, with your | separator's.
Took me quite some time to figure out that I needed //| to get a |.
All together did it take more time as I thought.

My time's up for the day so this is what I have:
Java
[php]
import java.awt.BorderLayout;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;
import java.io.BufferedReader;
import java.io.File;
import java.io.FileReader;
import java.util.ArrayList;

import javax.swing.JButton;
import javax.swing.JCheckBox;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JPanel;


public class MpP{
	/** Instance variables*/
	private String file="my_songs.txt";
	private ArrayList<String> playlist;
	private int track=0;
	Reader fr;
	private boolean shuf=false;
	private boolean rep=false;

	JPanel topPanel;
	JPanel bottomPanel;
	JPanel buttonPanel;
	JPanel checkPanel;
	JPanel selectPanel;

	JLabel text;
	JLabel status;

	JButton playB;
	JButton pauseB;
	JButton nextB;
	JButton prevB;
	JButton selectFileB;

	JCheckBox shuffleC;
	JCheckBox repeatC;

	/**Constructor*/
	MpP(){
		Reader fr=new Reader();
		gui();
	}

	void gui(){ /** All the gui stuff */
		/** A frame to stick panels on */
		JFrame frame=new JFrame();

		/** Panels to stick the components on */
		topPanel=new JPanel();
		bottomPanel=new JPanel();
		buttonPanel=new JPanel();
		checkPanel=new JPanel();
		selectPanel=new JPanel();

		/** Label to display the text */
		text=new JLabel();
		text.setText("Welcome to beginner challange #4!");
		status=new JLabel();
		status.setText("File loaded");

		/** Buttons with their text */
		playB=new JButton("play");
		pauseB=new JButton("pause");
		nextB=new JButton("next");
		prevB=new JButton("prev");
		selectFileB=new JButton("read file");

		/** The checkboxes */
		shuffleC=new JCheckBox("shuffle: off");
		repeatC=new JCheckBox("repeat: off");

		/** Selecting a layout where to put the components
		 * (with borderlayout, the options are NORHT, EAST, CENTER, WEST, SOUTH) */
		BorderLayout b=new BorderLayout();
		FlowLayout f=new FlowLayout();

		/** Stick the panels to the frame and some frame options */
		frame.getContentPane().add(b.NORTH, checkPanel);
		frame.getContentPane().add(b.CENTER, topPanel);
		frame.getContentPane().add(b.SOUTH, bottomPanel);
		frame.setSize(500,250);
		frame.setVisible(true);
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

		/** Fill the panels (every swing compontent can contain a maximum
		 * of five other components, thats why I use multiple panels) */
		topPanel.add(b.CENTER, text);
		topPanel.add(b.NORTH, status);
		bottomPanel.add(b.SOUTH, buttonPanel);
		checkPanel.setLayout(f);
		checkPanel.add(shuffleC, f.LEFT);
		checkPanel.add(repeatC, f.LEFT);
		buttonPanel.setLayout(f);
		buttonPanel.add(selectFileB, f.LEFT);
		buttonPanel.add(prevB, f.LEFT);
		buttonPanel.add(nextB, f.LEFT);
		buttonPanel.add(pauseB, f.LEFT);
		buttonPanel.add(playB, f.LEFT);

		/** register Listeners that wait for an event, to the buttons and checkboxes  */
		playB.addActionListener(new PlayListener());
		pauseB.addActionListener(new PauseListener());
		nextB.addActionListener(new NextListener());
		prevB.addActionListener(new PrevListener());
		selectFileB.addActionListener(new SelListener());
		shuffleC.addItemListener(new ShuffleListener());
		repeatC.addItemListener(new RepeatListener());

		go(file);
	}
	/**The listeners for the different buttons*/
	class PlayListener implements ActionListener{
		public void actionPerformed(ActionEvent event){
			status.setText("Playing...");
			playB.setEnabled(false); /**Disable the play button*/
			pauseB.setEnabled(true); /**Enable the pause button*/
			play();
		}
	}
	class PauseListener implements ActionListener{
		public void actionPerformed(ActionEvent event){
			playB.setEnabled(true);
			pauseB.setEnabled(false);
			status.setText("paused, press play to continue");
		}
	}
	class NextListener implements ActionListener{
		public void actionPerformed(ActionEvent event){
			if(shuf==false && rep==false){
				setTrack((getTrack()+1));
			}else if(rep==true){
				play();
			}else{
				shuffle();
			}
		}
	}
	class PrevListener implements ActionListener{
		public void actionPerformed(ActionEvent event){
			if(shuf==false && rep==false){
				setTrack((getTrack()-1));
			}else if(rep==true){
				play();
			}else{
				shuffle();
			}
		}
	}
	class SelListener implements ActionListener{
		public void actionPerformed(ActionEvent event){
			String file1=JOptionPane.showInputDialog(null, "Enter a filename to open: ", "bla", JOptionPane.QUESTION_MESSAGE);
			go(file1);
		}
	}
	public class ShuffleListener implements ItemListener{
		public void itemStateChanged(ItemEvent ev){
			if(shuf==false){
				shuffleC.setText("Shuffle: on");
				shuf=true;
				repeatC.setText("Repeat: off");
				rep=false;
				shuffle();
			}else{
				shuffleC.setText("Shuffle: off");
				shuf=false;
			}
		}
	}
	public class RepeatListener implements ItemListener{
		public void itemStateChanged(ItemEvent ev){
			if(rep==true){
				repeatC.setText("Repeat: off");
				rep=false;
			}else{
				repeatC.setText("Repeat: on");
				rep=true;
				shuffleC.setText("Shuffle: off");
				shuf=false;
			}
		}
	}

	void go(String file1){
		fr=new Reader();
		playlist=fr.readFile(file1);
		if(playlist.toString().equals("[Error]")){ /**What to do when the file cant be loaded?*/
			if(file1.equals(this.file)){
				status.setText("File not found: "+ file);
			}else{
				text.setText("File not found: "+file1);
				status.setText("Reloading: "+file);
				go(this.file);
			}

		}else{
			status.setText("File loaded "+this.file);
			this.file=file1;
		}
		fr=null;
	}

	void play(){
		String fullTrack=(String) playlist.get(getTrack());
		/**took me "some time" (many time actually) to realise that for splitting on a "|" is "//|" */
		String[] splitTrack=fullTrack.split("\\|");
		if (splitTrack.length!=3){
			status.setText("Error: Cant read track! "+splitTrack.length);
		}else{
			text.setText("Artist: "+splitTrack[0]+" Album: "+splitTrack[1]+" Track: "+splitTrack[2]);
		}
	}

	void shuffle(){
		setTrack((int) (Math.random()*(playlist.size()-1)));
		play();
	}

	void setTrack(int track){
		while(track<0){
			track=playlist.size()+track;
		}
		while(track >= playlist.size()){
			track=track-playlist.size();
		}
		this.track=track;
		play();
	}

	int getTrack(){
		return this.track;
	}
/**
 *** File reader innerclass (squeezed the classes in one file) ***
 */

	class Reader{
		/** (empty, default) instance variables */
		private ArrayList playlist;

		/** THE file-reader-methode */
		public ArrayList readFile(String fileName){
			playlist=new ArrayList();
			try{
				/**Make a chain to connect to the file*/
				File file=new File(fileName);
				FileReader fileReader = new FileReader(file);
				BufferedReader reader = new BufferedReader(fileReader);

				String line=null;
				while((line=reader.readLine()) !=null){
					playlist.add(line); /**Put the songs in an arraylist*/
				}
				reader.close(); /**Closing the top of the chain, coloses them whole chain*/
			}catch(Exception ex){ /**What to do when we have an error*/
				playlist.add("Error");
			}finally {
				return playlist;
			}
		}
	}
/**
 *** End of FileReader class ***
 */

	public static void main(String[] args) {
		MpP mpP=new MpP();

	}

}

[/php]

> **ZuLuuuuuu said:**
> Please specify how to compile/run your program if it is not written in a regular language like C/C++/Perl/Python/Ruby/Tcl.

Java not a regular language? :p
Make the file => $gedit MpP.java
Pass the code in.
To compile it => $javac MpP.java
To run it => $java MpP
Dont look at the warnings... :p

If someone has some hints or tips for me, please let me know!

NOTE: The .txt file must be in the same directory as the MpP file.

---

### Post by puddinlover on 2009-05-12
I could do this in PHP but since I'm starting to learn python I should be able to have this done in python within 3 weeks hehe.  I will post it here when I'm done.

---

### Post by gtr32 on 2009-05-16
This would be a good opportunity to use relational dataset instead of text document. I created a simple GUI with data input as well as save/load menus in a few minutes. Playback/Stop/Pause are not fully implemented as I didn't have more time than that. Unfortunately the data binding functionality does not work in Mono (unfixed bug in Mono framework) so for now this is a Windows only solution.

The attached exe should work with .NET 2.0 in Windows (have not tried Windows in VirtualBox but should work as well). Throws an error in Mono but if someone has the latest Mono version, I would appreciate if they would try it. I will post source code with comments later when I have time to implement the missing features.

---

### Post by jimi_hendrix on 2009-05-16
i refuse to partake in this challenge...there is no jimi hendrix in the playlist

---

### Post by snova on 2009-05-16
This probably works.

[PHP]
#!/usr/bin/python
# -*- coding: utf-8 -*-

import random
import readline
import sys

songs = [line.strip().split(" | ") for line in open("my_songs.txt")]
ordered = songs[:]
shuffle = False
current = 0
repeat = False

def nowPlaying():
    print "Now playing: %s - %s" % (songs[current][2], songs[current][0])

while True:
    try:
        command = raw_input("Enter command: ").strip().lower()
    except (KeyboardInterrupt, EOFError):
        exit()

    if command == "play":
        nowPlaying()
    elif command == "pause":
        print "Paused"
    elif command == "next":
        if not repeat:
            current += 1
        nowPlaying()
    elif command == "shuffle":
        shuffle = not shuffle
        if shuffle:
            random.shuffle(songs)
            print "Shuffle: on"
        else:
            songs = ordered[:]
            print "Shuffle: off"
    elif command == "repeat":
        repeat = not repeat
        if repeat:
            print "Repeat: on"
        else:
            print "Repeat: off"
    else:
        print "Unknown command."
[/PHP]

Save and run.

---

### Post by ZuLuuuuuu on 2009-05-17
@jimi_hendrix :)

Thanks for the people who posted their solutions so far. Keep up the good work.

I haven't tried the solutions so far except snova's (I'll try all of them don't worry*). Just wanted to say that snova's solution is perfectly valid so that you can see that the challenge is actually not that harder than previously posted challenges ;) (and snova's solution implements even the extra features, when you take off that features it reduces by 18 more lines!).

* gtr32, I am not sure if running a closed source program is a good idea (especially if it is Windows only). But I can try it after you post the source code. And a question to @Bodsda, are Windows only solutions acceptable? gtr32 says that it doesn't work on Mono but it works on Windows Framework 2.0.

---

### Post by s.fox on 2009-05-17
Oh,

This looks like a bit of fun.  I'll give this a go later.   Probably in a web scripting language like PHP....

-Ash R

---

### Post by elCabron on 2009-05-17
> **gtr32 said:**
> 
The attached exe should work with .NET 2.0 in Windows (have not tried Windows in VirtualBox but should work as well). Throws an error in Mono but if someone has the latest Mono version, I would appreciate if they would try it. I will post source code with comments later when I have time to implement the missing features.


I tried it with mono 2.4, which throws an exception. Didn't try it with the latest version built from trunk.

---

### Post by gtr32 on 2009-05-17
> **ZuLuuuuuu said:**
> 
* gtr32, I am not sure if running a closed source program is a good idea (especially if it is Windows only).

I didn't post it to be part of the challenge. I will post the source code and a few steps on how to create the datasets when I have more time, now I only had a few minutes. 

I do my GUI builds on Visual Studio as it still is by far the best IDE out there. The things I did in a few minutes would take considerably more time without VS. I did it for 2.0 framework to try be Mono compliant but unfortunately that bug (non-implementation) does exist so for now it won't work in Linux.

---

### Post by Bodsda on 2009-05-17
> **ZuLuuuuuu said:**
> @Bodsda, are Windows only solutions acceptable? gtr32 says that it doesn't work on Mono but it works on Windows Framework 2.0.

I would be inclined to say that it is at your discretion, however, as these challenges are for the benefit of beginner programmers, If the code cannot be understood by the beginner then it should not be included in the judging. The code cannot be verified by anyone unless they are used to developing on a .NET framework. So it's up to you but If your asking my opinion then I would leave it out of the judging (sorry gtr32) but I would definitely mention it at the end for the benefit of any beginner .NET programmers. 
 
Thanks,

Bodsda

---

### Post by gtr32 on 2009-05-17
> **Bodsda said:**
> as these challenges are for the benefit of beginner programmers

That's the reason why I'm posting. I saw the concerned post and thought I'd post something that was done in just a few steps. If I have time I will try to make either mono compliant source, or do it in C++, but anyways I will post more details later. For now, I just wanted someone to try it on latest Mono builds to see if the bug was fixed. I installed 2.4 on my machine last night and it's giving the same error.

---

### Post by wrtpeeps on 2009-05-17
> **Bodsda said:**
> erm... I'l give this a go, I think I could manage it, but i definitely cant do all of the extra credit bits. 

Remember this is a 'beginner' programming challenge not an intermediate or medium skill programming challenge.

I can't be bothered coding it, but if you want a tip (and I might be wrong but here goes) how I'd do it, I'd create 4 classes.

Song, album, artist, playlist.

Then I'd have like, album.add(Song mysong) , artist.add(Album whatever), playlist.add(artist).

Just thought that up in like 5 seconds, so no doubt there are shortcomings in it and it'd need refined, but it's help none the less. ;)

---

### Post by Bodsda on 2009-05-22
Ok, heres my attempt in python, dunno how good it is so all comments/suggestions are wlecome. (I know im using globals but i couldnt think of any other way of interacting with those vars)

[php]
#! /usr/bin/env python

import os
import random
import time

song_index = 0
status = 0              # Legend: 0 = Normal, 1 = Shuffle, 2 = Repeat
memory = 0

list = open("my_songs.txt").readlines()

def clear():
    os.system('clear')

def input(command):
    global status               # These are needed to stop the creation of local variables in this function
    global song_index
global memory
 
    if song_index == len(list):
        song_index = 0
        input("play")

    if command == "play":
        print "Playing: %s" % (list[song_index])

    elif command == "pause":
        print "Paused."

    elif command == "next":

        if status == 0:
            song_index += 1
            input("play")

        elif status == 1:
            song_index = random.randrange(len(list))
            input("play")

        elif status == 2:
            input("play")

    elif command == "shuffle":
        if status != 1:
            memory = status
            print "Status: Shuffle on"
            status = 1
        else:
            print "Status: Shuffle off"
            status = memory
    elif command == "repeat":
        if status != 2:
            memory = status
            print "Status: Repeat on"
            status = 2
        else:
            print "Status: Repeat off"
            status = memory
    elif command == "quit" or command == "exit":
        print "Thanks for using my mock audio player."
        time.sleep(0.5)
        exit()

    else:
        clear()
        print " Welcome to Bodsda's mock audio player. "
        print "========================================"
        print "\n\n\t Help\n\t======"
        print "\n\tPlay: Starts or resumes play"
        print "\n\tPause: Pauses play"
        print "\n\tNext: Plays next song"
        print "\n\tShuffle: Changes status to shuffle on"
        print "\n\tRepeat: Changes status to repeat on."
        print "\n\tQuit or Exit (self explanatory)\n"

def main():
    clear()

    print " Welcome to Bodsda's mock audio player. "
    print "========================================"

    while True:
        input(raw_input("Command: ").lower())           # Passes the input to the variable command used in input(command) function

main()
[/php]

Thanks,

Bodsda

---

### Post by smartbei on 2009-05-22
@Bodsda: globals are not too bad in this type of script, but I think you have a bug with the status variable. If someone first shuffles, and then wants to hear a certain song a couple times, so he repeats, and then turns off repeat to continue the playlist, he probably means for the shuffle to still be on...

Also, what happens when someone inputs 'next' 63 times? :-/

@snova - that last applies to you as well :-)

---

### Post by Bodsda on 2009-05-22
> **smartbei said:**
> @Bodsda: globals are not too bad in this type of script, but I think you have a bug with the status variable. If someone first shuffles, and then wants to hear a certain song a couple times, so he repeats, and then turns off repeat to continue the playlist, he probably means for the shuffle to still be on...

Also, what happens when someone inputs 'next' 63 times? :-/

@snova - that last applies to you as well :-)

As for the status bug, i think that should be fixable

re: the 63 times, dunno, im testing now

ty for the responses though,

Thanks,

Bodsda

---

### Post by Bodsda on 2009-05-22
Ok, both bugs fixed hopefully,

Thanks for pointing them out smartbei

Regards,

Bodsda

---

### Post by ZuLuuuuuu on 2009-05-26
Thanks for the solutions so far. As you might calculated, this is the last week for submissions and I'll review all the solutions this weekend, hopefully saturday ;)

---

### Post by Bodsda on 2009-05-26
Sounds good, I look forward to seeing the results.

Just to let everyone know, I have an important announcement concerning these challenges, which will be announced at the beginning of challenge #5. 

Regards,

Bodsda

---

### Post by bobbocanfly on 2009-05-26
I've written up a program that matches this brief, though not being a beginner, I don't think I should post it yet. 

Some ideas for extra things to implement if you get bored:
- Multiple commands per input (like the "&&" operator in bash) so "shuffle && next && shuffle" would shuffle a single song. Shouldn't be too difficult if you are handling commands in a sane way
- A status command that shows the current status of the player (shuffle on or off, repeat on or off etc.)
- Allow arguments to commands so "next 5" would skip the next 5 songs etc.

---

### Post by Bodsda on 2009-05-26
> **bobbocanfly said:**
> I've written up a program that matches this brief, though not being a beginner, I don't think I should post it yet. 

Some ideas for extra things to implement if you get bored:
- Multiple commands per input (like the "&&" operator in bash) so "shuffle && next && shuffle" would shuffle a single song. Shouldn't be too difficult if you are handling commands in a sane way
- A status command that shows the current status of the player (shuffle on or off, repeat on or off etc.)
- Allow arguments to commands so "next 5" would skip the next 5 songs etc.

Sounds like it could be interesting to do. I think my program already displays the status with the 'status' command so the && and next 5 would be my goal, I think I'm going to implement the next 5 one first, it shouldn't take too long, just a loop that iterates performing 'next' as many times as the number indicates. 

The && might be a bit of a problem, not sure how I would go about that yet... I'l have a think on it later. Thanks for the ideas bobbocanfly

@ZuLuuuuuu
Would doing some of the things that bobbocanfly just mentioned count as extra credit? If so everyone should definately at least think about adding the status command, thats the easiest of the three I reckon.

Regards,

Bodsda

---

### Post by ZuLuuuuuu on 2009-05-26
> **Bodsda said:**
> @ZuLuuuuuu
Would doing some of the things that bobbocanfly just mentioned count as extra credit? If so everyone should definately at least think about adding the status command, thats the easiest of the three I reckon.

Yes, actually you can add whatever command you want to get extra credit but bobbocanfly's ideas are pretty delicious :)

---

### Post by Bodsda on 2009-05-26
> **ZuLuuuuuu said:**
> Yes, actually you can add whatever command you want to get extra credit but bobbocanfly's ideas are pretty delicious :)

Cool, il make a start on it after my interview tomorrow.

btw, I was thinking for anyone else adding extra bits, a repeat all command was one of the extra credit suggestions ZuLuuuuuu made, but how about a repeat one command, which as the name suggests just repeats the current song once, or perhaps have one that repeats every song once.

Regards,

Bodsda

---

### Post by s.fox on 2009-05-27
Hi,

Here is my entry.  Its a healthy mix of PHP and Javascript.  My overall Javascipt knowledge isn't that great and its still a little buggy.   To start things off you need to click on a track.  Controls can be found at the bottom of the screen.  This was written two scripts which can be found below,  or you could run it via [this]("http://serial-coder.co.uk/testing/challenge/") link.

Code can be found in paste bin links: [index.php]("http://pastebin.com/m4ca47732") and [shuffle.php]("http://pastebin.com/m582ff56f")

Like I say its not perfect and known bugs include clicking Next twice in a row does not work and a similar problem with clicking Previous.  The code isn't especially neat but its more or less there.  I don't think I am going to get much time to invest in fixing these bugs.   On reflection I suppose I could have gotten away with having a single script when shuffling the tracks.  But never mind.  I enjoyed the challenge and I think it helped me improve my Javascript knowledge.  Maybe on the next challenge I'll pick a language that I am more knowlegeable in.  

-Ash R

P.S.   If anyone wants to have a go at improving/  bug fixxing my scripts feel free.  If you do please post your changes,  as I am keen to see how these problems were fixed.  Thanks.

---

### Post by matmatmat on 2009-05-27
Can I build on Snova's code?

---

### Post by Bodsda on 2009-05-27
> **matmatmat said:**
> Can I build on Snova's code?

I suppose you would have to ask Snova, but it shouldn't take long to hack something together like Snova's. If you join ##beginners-dev on irc.freenode.net someone there may be happy to help you get started.

---

### Post by matmatmat on 2009-05-27
I've just changed it to support the extrat stuff:
```

shuffle && repeat
next 5

```

---

### Post by Bodsda on 2009-05-27
> **matmatmat said:**
> I've just changed it to support the extrat stuff:
```

shuffle && repeat
next 5

```

Well done, now all you need to do is write the base code or talk to Snova.

---

### Post by matmatmat on 2009-05-27
This is mine (sorry if it's to much like Snova's!) :
```

#!/usr/bin/python
# -*- coding: utf-8 -*-

import random
import sys

songs = [line.strip().split(" | ") for line in open("my_songs.txt")]
ordered = songs[:]
shuffle = False
current = 0
repeat = False

def nowPlayingP(current):
    global playstring
    try:
    	playstring = "Playing: %s | %s" % (songs[current][2], songs[current][0])
    except:
	print "The number passed was not valid, please use a lower number"
	return
    print playstring

def nowPlaying():
    global playstring
    playstring = "Now playing: %s | %s" % (songs[current][2], songs[current][0])
    print playstring

def help():
	print "Play      \t\tStart playing"
	print "Next      \t\tPlay next track"
	print "Next [num]\t\tGo forward [num] amount of tracks"
	print "Prev      \t\tPlay previous track"
	print "Prev [num]\t\tGo back [num] amount of tracks"
	print "Repeat    \t\tEnable repeats"
	print "Shuffle   \t\tEnable shuffle"
	print "Status    \t\tPrint currently playing track & wheather shuffle & repeat are enabled"
	print "List      \t\tList the songs in playlist"
	print "&&        \t\tUsed to join commands together (see examples)"
	print "Help      \t\tPrint this message out"
	print 
	print "Eg:"
	print "play && next 10 && list"
	print "status"
	print "play && shuffle && repeat"

while True:
    try:
        command = raw_input("Enter command: ").strip().lower()
    except (KeyboardInterrupt, EOFError):
        print 
        exit()

    if command == "play":
        nowPlaying()
    elif command == "pause":
        print "Paused"
    elif command == "next":
        if not repeat:
            current += 1
        nowPlaying()
    elif command == "prev":
	if not repeat:
	    current -= 1
	nowPlaying()
    elif command.split(" ")[0] == "next":
	oldcurrent = current
        current += int(command.split(" ")[1])
        if current > len(songs):
		print "The number you entered is more thant the number of songs!"  
		print "Just doing 'next' ('next 1') instead"           
		current = oldcurrent + 1		
        nowPlaying()
    elif command.split(" ")[0] == "prev":
	oldcurrent = current
        current -= int(command.split(" ")[1])
        if current > len(songs):
		print "The number you entered is invalid!"  
		print "Just doing 'prev' ('prev 1') instead"      
                current = oldcurrent - 1
	elif current < 0:
		print "The number you entered is invalid!"      
                current = 0		
        nowPlayingP(current)
    elif command == "shuffle":
        shuffle = not shuffle
        if shuffle:
            random.shuffle(songs)
            print "Shuffle: on"
        else:
            songs = ordered[:]
            print "Shuffle: off"
    elif command == "repeat":
        repeat = not repeat
        if repeat:
            print "Repeat: on"
        else:
            print "Repeat: off"
    elif command == "status":
        print playstring
        if shuffle:
                print "Shuffle: on"
        else:
                print "Shuffle: off"
        if repeat:
                print "Repeat: on"
        else:
                print "Repeat: off"
    elif command == "list":
	for l in songs:
		print l
    elif command == "help":
	help()
    elif len(command.split(" && ")) > 0:
	for i in command.split(" && "):
    		if i == "play":
        		nowPlaying()
   		elif i == "pause":
        		print "Paused"
    		elif i == "next":
        		if not repeat:
            			current += 1
        		nowPlaying()
		elif command == "prev":
			if not repeat:
	    			current -= 1
			nowPlaying()
    		elif i.split(" ")[0] == "next":
			oldcurrent = current
        		current += int(i.split(" ")[1])
        		if current > len(songs):
				print "The number you entered is more thant the number of songs!"  
				print "Just doing 'next' ('next 1') instead"      
				current = oldcurrent + 1
			nowPlaying()
    		elif i.split(" ")[0] == "prev":
        		current -= int(i.split(" ")[1])
			nowPlayingP(current)
    		elif i == "shuffle":
       		 	shuffle = not shuffle
        		if shuffle:
            			random.shuffle(songs)
            			print "Shuffle: on"
        		else:
            			songs = ordered[:]
            			print "Shuffle: off"
    		elif i == "repeat":
        		repeat = not repeat
        		if repeat:
            			print "Repeat: on"
        		else:
            			print "Repeat: off"
		elif i == "status":
        		print playstring
        		if shuffle:
                		print "Shuffle: on"
       		 	else:
                		print "Shuffle: off"
        		if repeat:
                		print "Repeat: on"
        		else:
               			print "Repeat: off" 
		elif i == "list":
			for l in songs:
				print l
		elif i == "help":
			help()
		else:
			print "Please enter a valid command"  
	
    else:
        	print "Please enter a valid command"  

```

---

### Post by snova on 2009-05-27
> **matmatmat said:**
> This is mine (sorry if it's to much like Snova's!) :

I can see the resemblance, but that's ok. :)

> ```

    elif len(command.split(" && ")) > 0:
	for i in command.split(" && "):

```

I only have one thing to mention, and it's that this construct results in a lot of duplicated code. Why not move the && code higher up?

```

while True:
    try:
        # Read a line, convert it to lowercase, split it at "&&", and strip spaces from each command.
        commands = [command.strip() for command in raw_input("Enter command: ").lower().split("&&")]
    except (KeyboardInterrupt, EOFError):
        print 
        exit()
    for command in commands:
        # Some of these commands take arguments, so split the line again.
        args = command.split()
        command = args.pop(0)

        if command == "play":
            nowPlaying()
        # ... As before ...
        elif command == "next":
    	    oldcurrent = current
            current += int(args[0]) # By the way, you might want to check this for validity
            if current > len(songs):
		print "The number you entered is more thant the number of songs!"  
		print "Just doing 'next' ('next 1') instead"           
		current = oldcurrent + 1		
        nowPlaying()
        # ...

```

Also, don't mix tabs and spaces in Python code. Use one or the other consistently- preferably the latter.

---

### Post by Bodsda on 2009-05-27
> **matmatmat said:**
> This is mine (sorry if it's to much like Snova's!) :
```



def nowPlayingP(current):
    global playstring
    try:
    	playstring = "Playing: %s | %s" % (songs[current][2], songs[current][0])
    except:
	print "The number passed was not valid, please use a lower number"
	return
    print playstring

def nowPlaying():
    global playstring
    playstring = "Now playing: %s | %s" % (songs[current][2], songs[current][0])
    print playstring

"  

```

Looking at both the now playing functions makes me wonder, does python support function overloading in the same way as C++?

def play()
def play(foo)
def play(foo,bar)

are all different but the same, if you see what I mean.

---

### Post by snova on 2009-05-27
> **Bodsda said:**
> Looking at both the now playing functions makes me wonder, does python support function overloading in the same way as C++?

def play()
def play(foo)
def play(foo,bar)

are all different but the same, if you see what I mean.

No.

---

### Post by Bodsda on 2009-05-27
> **snova said:**
> No.

Well thats just stupid. :(

---

### Post by sujoy on 2009-05-28
oh boy. nope

python, when given multiple functions with the same name, will silently ignore the rest and just use the last declaration. how can you possibly infer type and do function overloading based on it in a duck typed language!! hence it wont work

---

### Post by crdlb on 2009-05-28
You can use default arguments to implement that specific example though:

```
def play(foo=None, bar=None):
    if foo is not None:
        # do stuff with foo
    if bar is not None:
        # do stuff with bar

```

---

### Post by ZuLuuuuuu on 2009-05-30
Ok, here is the winner:















Heh, I just started reading the codes, so sit tight :) I'll post the winner in a few hours.

---

### Post by ZuLuuuuuu on 2009-05-30
Ok, I looked at the code of participants. Thank you all for your effort. You all done a great job. But somebody should have been declared as winner. And here it is:

[CENTER][COLOR="Purple"][SIZE="6"]snova[/SIZE][/COLOR][/CENTER]

Congratulations snova!

I took some notes about the codes.

Froodolt's code is very nice and the program is very fun to play with. Thanks for the great effort. But it has some element in it which makes it not so beginner level (it is a compliment actually).

snova's code was the most clean code. No code repetition and the algorithm was clean and working the way I wanted. It had even implemented the extras. The solution is pretty simple so the code mostly doesn't need comments in it but a few comments would have been better. The input file was already organised well but using split to format it as you want is both a beginner level and neat trick.

Bodsda's code has a syntax error in it about indenting (line 19) it was a negative point but I fixed it and then continued looking. The user interface was very clean for a command line program thanks to the .clear method he used, the organization of other elements and the quit message with time.sleep. Bodsda certainly has an artist soul in him! He implemented the extra features, too. Using *memory* variable not to use 2 variables separately for repeat and shuffle is another approach by Bodsda. But it might be a better approach to use two seperate variables so that the algorithm was simpler (for this problem particularly, for another problem your approach might be better). Thanks for the comments in the code.

matmatmat's program was the most featured one but, unfortunately, the code was not so clean. Mixed indentations considered harmful for Python as far as I know. Also there are long duplicated codes as snova pointed out. Thanks, for the effort to build the most featured player though!

Ash R's idea to make it a web site was pretty original in this challenges and also pretty popular these days because of Web 2.0 concept. Though the implementation was a little buggy as he pointed out. The bugs are mainly because he depent on HTML too much, maybe he could keep the songs in a data structure and it would give him the opportunity to implement the algorithms without depending on HTML ids, hidden inputs etc.. As himself noted, making the two pages one would be much better. If Ash R improves his Javascript knowledge then he might be a really serious challenger for the next challenges with "program as a web page" thing :)

A general advice for Python users: in snova's code you can see a line like "import readline". This makes using the command line easier since you can edit your command by moving cursor back and forth and also enter a previously executed command again by using up arrow. Though I didn't gave extra points to this feature cause it might require some experience to know such a trick :)

So, now the duty to prepare "Beginner programming challenge #5" is snova's. I hope you had fun with implementing this program. Thanks to Bodsda for the idea of restarting the beginner challenges...

---

### Post by s.fox on 2009-05-30
Hi,

I just wanted to say thank you ZuLuuuuuu for the positive critique of my code.   Next time I am going to implement something in a language i am comfortable with,  then maybe if i get time persevere with javascript.  :)  

I await the next challenge with much enthusiasm. :)

-Ash R

---

### Post by Bodsda on 2009-05-31
Congratulations Snova!

@Zuluuuuuu: Thanks a lot for the detailed explanations, and as for the indent error, it was probably a copy and paste error due to the comments spanning > 80 chars, my bad. Thanks for all the constructive criticism though :)

I look forward to participating in challenge #5, and dont forget, I'm making the announcement as soon as the challenge is posted! :)

Thanks,

Bodsda

---

### Post by gtr32 on 2009-05-31
Snova, please post a link to the next challenge when it is posted. Thanks, and congrats!

---

### Post by bobbocanfly on 2009-05-31
Now the challenge is over I'll post up my code. I'm not quite a beginner, so didn't feel right entering it. 

```
#!/usr/bin/env python

import random

class Song:
	""" Represents a single song """

	def __init__(self, artist="", album="", title="", uid=0):
		self.artist = artist.strip()
		self.album = album.strip()
		self.title = title.strip()
		self.id = uid

	def __str__(self):
		return "'%s' by %s from the album %s" % (self.title, self.artist, self.album)

class Player:
	""" The primary player class. Does all the "playing". Well not really """

	def __init__(self, fname):
		# Some vars to control the "playback"
		self.tracks = []
		self.playing = False 
		self.repeat = False
		self.repeat_single = False
		self.shuffle = False
		self.current = 0

		# Setup the database
		uid = 0

		for line in open(fname):
			split = line.split("|")
			self.tracks.append(Song(split[0], split[1], split[2], uid))
			uid += 1

		# We have our database, now enter the control loop
		command = ""

		while command != "exit":
			try:
				command = raw_input(">>> ").lower()

				if command != "exit":
					self.parse_command(command)
			except KeyboardInterrupt:
				command = "exit"

	def parse_command(self, c):
		""" Parses the user's input and calls the correct command callback function """
		for command in c.split("&&"):
			base = command.strip().split()

			try:
				command = base[0]
			except:
				pass

			try:
				arg = base[1]
			except:
				arg = None
		
			if "cb_%s" % command in dir(self):
				exec "self.cb_%s(arg)" % command
			else:
				print "Unknown command"
		
	def cb_play(self, arg):
		""" Callback for the "play" command. No args """
		if not self.playing:
			self.playing = True

		print "Now Playing: %s" % str(self.tracks[self.current])

	def cb_next(self, arg):		
		""" Callback for the next command. Arg is the number of songs to skip """
		if not self.repeat:
			if not self.shuffle:
				if not arg:
					jump = 1
				else:
					try:
						jump = int(arg)
					except TypeError:
						print "Invalid argument, must be a number"
						return

				self.current = (self.current + jump) % len(self.tracks)
			else:
				self.current = random.randint(0, len(self.tracks)-1)

		if self.repeat_single:
			self.cb_repeat(None)

		self.cb_play(None)

	def cb_previous(self, arg):
		if not arg:
			arg = -1
		else:
			# Is there an easier way to convert 2 into -2 in Python?
			try:
				arg = int(arg) - (2 * int(arg))
			except TypeError:
				print "Invalid argument, must be a number"
				return

		self.cb_next(arg)

	def cb_pause(self, arg):
		""" Callback for the pause command. Pauses playback """
		if self.playing:
			self.playing = False
			print "Paused"

	def cb_repeat(self, arg):
		""" Repeat command callback. Defines repeat mode """
		if arg == "-s":
			self.repeat_single = True
		else:
			self.repeat_single = False

		self.repeat = not self.repeat
		print "Repeat mode %s %s" % (["off", "on"][self.repeat], ["", "(single track)"][self.repeat_single])

	def cb_shuffle(self, arg):
		""" Shuffle command callback. Defines shuffle mode """
		self.shuffle = not self.shuffle
		print "Shuffle mode %s" % ["off", "on"][self.shuffle]

	def cb_status(self, arg):
		""" Status command callback. Prints the player's current status """
		print "Shuffle mode %s" % ["off", "on"][self.shuffle]
		print "Repeat mode %s %s" % (["off", "on"][self.repeat], ["", "(single track)"][self.repeat_single])
		print "%s songs loaded into the library" % len(self.tracks)
		
		if self.playing:
			print "Currently playing %s" % str(self.tracks[self.current])
		else:
			print "Player currently paused"

if __name__ == "__main__":
	Player("my_songs.txt")
```

This has made me want to create a "shell" like music player. I may look at hacking a music playing backend onto my code and posting it up for anyone else that would be interested in something similar (that actually plays the songs, of course :P)

---

### Post by ZuLuuuuuu on 2009-06-02
Is snova aware that he is the winner? :)

---

### Post by snova on 2009-06-02
> **ZuLuuuuuu said:**
> Is snova aware that he is the winner? :)

The mob coming after me makes it difficult to forget.

Ideas, ideas, ideas... I think I have one.

---

### Post by Joeb454 on 2009-06-02
> **snova said:**
> The mob coming after me makes it difficult to forget.

Ideas, ideas, ideas... I think I have one.

Post it, I may even have a go ;)

---

### Post by snova on 2009-06-02
> **Joeb454 said:**
> Post it, I may even have a go ;)

"Challenge #5: Help me come up with Challenge #6"

[http://ubuntuforums.org/showthread.php?t=1176793](http://ubuntuforums.org/showthread.php?t=1176793)

---

### Post by exutable on 2009-08-23
It appears pymedia would be great for this [http://pymedia.org/tut/]("http://pymedia.org/tut/")

---

