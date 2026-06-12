---
title: "[SOLVED] Another Scripting Question"
date: 2007-10-15
forum: Programming Talk
---

### Post by kast on 2007-10-15
I've been reading up on shell scripting, and I'm thinking of silly scripts to write to help cement some of the things I have been reading. I decided one script I could write would run a command to start a camera capture, and then once the file/folder gets to a certain size the script will then find the process and kill it and then proceed to move the file. 
i have the code to detect the size and find and kill process etc.., but if i  run the camera command in the script it just kicks off and never returns to the next line of code. is there any way to get this command to maybe spawn into another shell? or do i just have to run the camera command separate from the Process capture and kill script?

So first things the script will do is kick of the capture

[B]mencoder tv:// -tv 
driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi[/B]

I put that in a variable and name it what ever.

At this point it just runs away, i understand why this happens, but not a way around it. I know I could find and option in the capture command to stop at a certain size, but that would kill the hole point of writing the script to learn.

I would like the script to return and go to the next line of code, below is some of the code, minus the file move options Thanks!

[COLOR="Blue"]#

# Find File size and name, Then test folder size

# If the folder is over set size kill process

#[/COLOR]



[B]find /media/backup/cam -printf '%s %p\n' | while read size name; do

    

    if [ "$size" -lt 600000 ] 

    then

          sleep 15

    else 

          echo "Process Has not been started yet!"

    fi

done[/B]



[COLOR="Blue"]#       

# Killing Camera Capture Process after folder reached set size

#       [/COLOR]

       [B]echo "Killing Process..."

       kill "$pid"   

       exit 1[/B]

# End Script

---

### Post by weresheep on 2007-10-15
Hello,

If you add an ampersand (&) to the end of your camera command the shell will run the command in the background and return control to your script.

So...

```
mencoder ... -o webcam.avi
```

becomes

```
mencoder ... -o webcam.avi &
```

In addition, when you run a command with & the shell returns the process ID of that command. This can be seen by running 'ls &' at the command prompt. I get for example

```
gavin@strathconon:~$ ls -l &
[1] 5557

```

Hope that helps.

-weresheep

---

### Post by kast on 2007-10-15
Thanks for the reply! 

 i have tried the & sigh with the Camera command, but it doesn't place it in the back ground. the only explanation i can think of is that there must be something with in the capture command that stops this?

when i run 

**mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi&**

i get

[I]CPU: Intel(R) Pentium(R) 4 CPU 2.66GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: Logitech QuickCam Notebook Pro
 Capabilites: capture 
 Device type: 1
 Supported sizes: 160x120 => 640x480
 Inputs: 1
  0: Webcam:  (tuner:0, norm:pal)
Using input 'Webcam'
Selected input hasn't got a tuner!
[V] filefmt:9  fourcc:0x32315659  size:320x240  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 705.6 kbit/100.00% (ratio: 88200->88200)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (320x240 fourcc=34504d46 [FMP4])
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
MP3 audio selected.
Forcing audio preload to 0, max pts correction to 0.
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
[/I]

then it starts to capture and the screen will fly by with 

[I]6 duplicate frame(s)!
Pos:   0.4s      4f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
4 duplicate frame(s)!
Pos:   0.7s      7f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
5 duplicate frame(s)!
Pos:   1.0s     10f ( 0%)  8.38fps Trem:   0min   0mb  A-V:0.000 [0:0]
4 duplicate frame(s)!
Pos:   1.3s     13f ( 0%)  8.77fps Trem:   0min   0mb  A-V:0.000 [2454:63][/I]
 
never actually places it in the back ground.

---

### Post by weresheep on 2007-10-15
Hi again,

I don't know if that was a typo but the & should be separated by a space. In your command above it was added directly to the end of file name.

It might be that the command is not actually be running in the background, but lets be sure...

When you issue a command with a trailing & the shell starts the command running in a new process and returns control the original process. However, the background process is still bound to the tty (terminal) that spawned it so any output it generates still appear on the terminal. You can test this be doing 'ls &'. The ls command is run in the background but its text still appears on screen.

One thing to try would be to run your camera command directly in a terminal, with the & but also redirect all output to /dev/null. So something like this...

```
mencoder ... -o webcam.avi &>1 /dev/null &
```

When you run this command, it **should** return control to the terminal straight away with the process ID of the command, but no other text should be displayed. If you then run top, you should see the mencoder command still running.

If the mencoder command isn't being run in the background then something else is going wrong.

Let me know if that doesn't make any sense.

-weresheep

---

### Post by kast on 2007-10-15
Sorry that was a typo

Still there is progress! when i run

*mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi &>1 /dev/null &*

in a shell by itself it now runs and goes in the back ground! but when i put that same command into the script,  it still doesn't return to the next line of code. i did notice i get a 

**./Cam_Cap: 45: /dev/null: Permission denied **

line 45: is where i have the new line

*mencoder ... -o webcam.avi &>1 /dev/null &*

Weird that running it by itself its fine, in the script its not. I'm having a feeling that this might not be as easy as i thought :)

---

### Post by slavik on 2007-10-16
fork and exec :)

---

### Post by weresheep on 2007-10-16
Hmm, I'm not too sure what could be happening. Could you post (or private message me) your script and I'll try running it on my machine?

Thanks,
-weresheep

---

### Post by kast on 2007-10-18
[I]#
# Test to see that Camera Capture is running
#[/I]

if  [ -z "$pid" ]
    then
        echo "Process Has not been started yet!"
        exit 1
fi

[I]#
# Find File size and name, Then test folder size
# If the folder is over set size kill process
#[/I]

find /media/backup/cam -printf '%s %p\n' | while read size name; do
    
if  [ "$size" -lt 5000 ] 
    then 
        sleep 15
    else
        echo "Killing Process..."
        kill "$pid"
fi
done

[I]#       
# Killing Camera Capture Process after folder reached set size
#[/I]

---

### Post by jpkotta on 2007-10-19
To redirect stdout in bash or Bourne shell (e.g. dash or sh):
```
noisy_command > /dev/null
```

To redirect stdout and stderr in bash:
```
noisy_command >& /dev/null
```

To redirect stdout and stderr in Bourne shell, or bash:
```
noisy_command >/dev/null 2>/dev/null
```

---

### Post by kast on 2007-10-19
jpkotta thanks for the reply! ill add that to my cam command and see how it goes when i get home, and post back.

---

### Post by kast on 2007-10-20
jpkotta Thank you, that did the trick!

**mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi >/dev/null 2>/dev/null &**

Works perfect thanks everyone!

---

