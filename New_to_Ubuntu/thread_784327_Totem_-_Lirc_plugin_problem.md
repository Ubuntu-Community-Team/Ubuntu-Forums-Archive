---
title: "Totem - Lirc plugin problem"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Cz-David on 2008-05-06
After two hours of frustration I finnaly get irw in cmd work with my remote control (serial home made lirc reciever) now when I try to enable lirc plugin in totem, I get this "Failed to initialize LIRC"... what is wrong with that ... also is there any other media player with lirc support ? or girder/uICE alternative ...

---

### Post by herbster on 2008-05-06
I have never used Totem, can't help you with that specifically. You are open to another media player with LIRC support-- I'd suggest VLC. You can edit the ~/.vlc/vlcrc config to include "control=LIRC" or run the program with:

```
vlc --control=lirc
```

Here's a portion of my ~/.lircrc for VLC:

```
#--------------------------------------------------
# vlc
#--------------------------------------------------

begin
        prog = vlc
        button = Play
        config = key-play-pause
        repeat = 0
end
begin
        prog = vlc
        button = Pause
        config = key-play-pause
        repeat = 0
end
```

You can do "vlc --help" for a list of key bindings.

---

### Post by Cz-David on 2008-05-06
seems it's working... thanks

---

### Post by sturmer on 2008-08-16
I am having the same problem...this is getting frustrating..i first thought that i didn't setup my lirc correctly but pc does respond to some of the commands (the sound commands,and numbers to be specific) but the rest of them are silent no media keys and i am using Happauge remote (and happauge IR-receiver) so can anyone help me?

---

### Post by herbster on 2008-08-19
sturmer, which **exact** remote/tuner card are you using? PVR-150, 300, etc.?

---

### Post by OffAxis on 2008-08-19
> i first thought that i didn't setup my lirc correctly but pc does respond to some of the commands (the sound commands,and numbers to be specific)
if some commands are working and others aren't then there's a problem with one (or more) of these...
1. your /etc/lirc/lircd.conf file
2. the ~.lircrc file (which may be in the ~./lirc/ folder)
3. your remote control buttons
4. Interference from an external light source

you can run
```
irw
```

from the command line and press the buttons on the remote, and make sure that every key press has some output (Ctrl+C will get you back to a prompt). If that works then that means #1, #3 and #4 are good, so your problem is #2. Can you post your .lircrc file?

---

### Post by sturmer on 2008-08-19
Ok i am sure that my remote works , because it works flawless in windows.

my lircd.conf file
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

```

and there is no file in folder, ~./lirc

as i see here the lircd.conf.happauge is this

the content of the lircd.conf.haupauge file

```
#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
#
# brand: 				Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg www.lugv.at
# 
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote


begin remote
  name            HVR-1100
  bits            16
  eps             30
  aeps            100
  one             0     0
  zero            0     0
  gap             135862
  pre_data_bits   16
  pre_data        0x8001

  begin codes
       Go              0x0161
       power           0x0074
       Tv              0x0179
       Videos          0x0189
       Music           0x0188
       Pictures        0x016F
       Guide           0x016D
       Radio           0x0181
       Up              0x0067
       Down            0x006C
       Left            0x0069
       Right           0x006A
       Ok              0x001C
       Back/edit       0x00AE
       Menu            0x008B
       Vol+            0x0073
       Vol-            0x0072
       PrevChan        0x019C
       Chan+           0x0192
       Chan-           0x0193
       Mute            0x0071
       Record          0x00A7
       Stop            0x0080
       replay          0x00A8
       SKip            0x00D0
       play            0x00CF
       Previous        0x00A5
       Next            0x00A3
       Pause           0x0077
       1               0x0002
       2               0x0003
       3               0x0004
       4               0x0005
       5               0x0006
       6               0x0007
       7               0x0008
       8               0x0009
       9               0x000A
       *               0x0184
       0               0x000B
       #               0x0172
       red             0x018E
       green           0x018F
       yellow          0x0190
       blue            0x0191

  end codes

end remote 
```


and my capture card is Hauppauge pci whit Cx88 chipset (if i remeber correctly)

---

