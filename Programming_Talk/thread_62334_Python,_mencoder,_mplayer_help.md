---
title: "Python, mencoder, mplayer help"
date: 2005-09-04
forum: Programming Talk
---

### Post by Drakx on 2005-09-04
Hi

as you know i'm trying my hardest to give quickrip life again ive fixed all seeable bugs just one section of code to do with mplayer/mencoder as im not too familiar with mencoder/mplayer im hoping some one will help me out till i get the hang of mencoder/mplayer the code that is not working is below:

```


# Clean up output dir in case QuickRip crashed out there
            os.popen("".join(["rm ", self.outdir, "frameno.avi 2>/dev/null"]))

            lameopts = "".join(["cbr=", str(self.track['abr']), str(self.vol)])
            if self.config['videocodec'] is 1:
                ovc = "xvid"
                ovc_opts_type = "-xvidencopts"
                ovc_opts = "".join(["4mv:me_quality=6:mod_quant:quant_range=1-31/1-31:bitrate=", str(int(self.track['vbr']))])
            else:
                ovc = "lavc"
                ovc_opts_type = "-lavcopts"
                ovc_opts = "".join(["vcodec=mpeg4:vhq:vbitrate=", str(int(self.track['vbr']))])
            vop = "".join(["scale,crop=",self.track['crop']])

            if int(self.config['deinterlacing']) is not 0:
                vop = "".join([vop, ",", self.dio[self.config['deinterlacing']]])
#############From here not working proerly############
            if self.config['passes'] is 1:
                all_pass = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-oac",  "mp3lame", "-lameopts", lameopts, "-ovc", ovc, ovc_opts_type, ovc_opts, "-vop", vop, "-zoom", \
                "-xy", resolution, "-o", self.output, "2>/dev/null"]
  
  
                if int(self.config['aspectratio']) is not 0:
                    all_pass.insert(3, "-aspect")
                    all_pass.insert(4, self.aro[self.config['aspectratio']])

                if self.sLanguage is not "None":
                    all_pass.insert(3, "-slang")
                    all_pass.insert(4, self.sLanguage)

                 # Uncomment to test command
#                 string = ""
#                 for bit in all_pass:
#                     bit = "".join([" ", bit])
#                     string = "".join([string, bit])
#                 print all_pass
#                 print string
#               sys.exit(1)

                self.runPass("audio", all_pass)

            elif not self.config['passes'] or self.config['passes'] is 2:
                audio_pass = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-oac",  "mp3lame", "-lameopts", lameopts, "-ovc", "frameno", "-o", \
                "".join([self.outdir, "frameno.avi"]), "2>/dev/null"]
  # added nice -n 3
                video_pass = [str(self.config['mencoder']),"-dvd", str(self.track['id']), "-alang", self.aLanguage, \
  "-sws", "2", "-oac", "copy", "-ovc", ovc, ovc_opts_type, "-vop", vop, "-zoom", "-xy", resolution, \
                "-o", self.output, "2>/dev/null"]
                
                if int(self.config['aspectratio']) is not 0:
                    video_pass.insert(3, "-aspect")
                    video_pass.insert(4, self.aro[self.config['aspectratio']])

                if self.sLanguage is not "None":
                    video_pass.insert(3, "-slang")
                    video_pass.insert(4, self.sLanguage)

#                 # Uncomment to test command
#                 string1 = ""
#                 string2 = ""
#                 for bit in audio_pass:
#                     bit = "".join([" ", str(bit)])
#                     string1 = "".join([string1, bit])
#                 for bit in video_pass:
#                     bit = "".join([" ", str(bit)])
#                     string2 = "".join([string2, bit])
#                 print string1
#                 print string2
#               sys.exit(1)

                self.runPass("audio", audio_pass)
                self.runPass("video1", video_pass)

                os.popen("rm divx2pass.log 2>/dev/null")
                os.popen("".join(["rm ", self.outdir, "frameno.avi 2>/dev/null"]))


            elif self.config['passes'] is 3:
                audio_pass = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-oac",  "mp3lame", "-lameopts", lameopts, "-ovc", "frameno", "-o", \
                "".join([self.outdir, "frameno.avi"]), "2>/dev/null"]
  
  video_pass1 = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-sws", "2", "-oac", "copy", "-ovc", ovc, ovc_opts_type, "".join([ovc_opts, ":vpass=1"]), "-vop", vop, \
                "-zoom", "-xy", resolution, "-o", self.output, "2>/dev/null"]
  
                video_pass2 = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-sws", "2", "-oac", "copy", "-ovc", ovc, ovc_opts_type, "".join([ovc_opts, ":vpass=2"]), "-vop", vop, \
                "-zoom", "-xy", resolution, "-o", self.output, "2>/dev/null"]
  
########## To here????##########################    
                if int(self.config['aspectratio']) is not 0:
                    video_pass1.insert(3, "-aspect")
                    video_pass1.insert(4, self.aro[self.config['aspectratio']])
                    video_pass2.insert(3, "-aspect")
                    video_pass2.insert(4, self.aro[self.config['aspectratio']])

                if self.sLanguage is not "None":
                    video_pass1.insert(3, "-slang")
                    video_pass1.insert(4, self.sLanguage)
                    video_pass2.insert(3, "-slang")
                    video_pass2.insert(4, self.sLanguage)

                self.runPass("audio", audio_pass)
                self.runPass("video1", video_pass1)
                self.runPass("video2", video_pass2)
                
                os.popen("rm divx2pass.log 2>/dev/null")
                os.popen("".join(["rm ", self.outdir, "frameno.avi 2>/dev/null"]))

        os.chdir(self.cwd)
        self.int_finishRipping()

```

the section that is not working is 

########### text #####################

########## text ######################

thanks

---

### Post by cwaldbieser on 2005-09-05
[QUOTE=Drakx]Hi

as you know i'm trying my hardest to give quickrip life again ive fixed all seeable bugs just one section of code to do with mplayer/mencoder as im not too familiar with mencoder/mplayer im hoping some one will help me out till i get the hang of mencoder/mplayer the code that is not working is below:

```


# Clean up output dir in case QuickRip crashed out there
            os.popen("".join(["rm ", self.outdir, "frameno.avi 2>/dev/null"]))

            lameopts = "".join(["cbr=", str(self.track['abr']), str(self.vol)])
            if self.config['videocodec'] is 1:
                ovc = "xvid"
                ovc_opts_type = "-xvidencopts"
                ovc_opts = "".join(["4mv:me_quality=6:mod_quant:quant_range=1-31/1-31:bitrate=", str(int(self.track['vbr']))])
            else:
                ovc = "lavc"
                ovc_opts_type = "-lavcopts"
                ovc_opts = "".join(["vcodec=mpeg4:vhq:vbitrate=", str(int(self.track['vbr']))])
            vop = "".join(["scale,crop=",self.track['crop']])

            if int(self.config['deinterlacing']) is not 0:
                vop = "".join([vop, ",", self.dio[self.config['deinterlacing']]])
#############From here not working proerly############
            if self.config['passes'] is 1:
                all_pass = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-oac",  "mp3lame", "-lameopts", lameopts, "-ovc", ovc, ovc_opts_type, ovc_opts, "-vop", vop, "-zoom", \
                "-xy", resolution, "-o", self.output, "2>/dev/null"]
  
  
                if int(self.config['aspectratio']) is not 0:
                    all_pass.insert(3, "-aspect")
                    all_pass.insert(4, self.aro[self.config['aspectratio']])

                if self.sLanguage is not "None":
                    all_pass.insert(3, "-slang")
                    all_pass.insert(4, self.sLanguage)

                 # Uncomment to test command
#                 string = ""
#                 for bit in all_pass:
#                     bit = "".join([" ", bit])
#                     string = "".join([string, bit])
#                 print all_pass
#                 print string
#               sys.exit(1)

                self.runPass("audio", all_pass)

            elif not self.config['passes'] or self.config['passes'] is 2:
                audio_pass = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-oac",  "mp3lame", "-lameopts", lameopts, "-ovc", "frameno", "-o", \
                "".join([self.outdir, "frameno.avi"]), "2>/dev/null"]
  # added nice -n 3
                video_pass = [str(self.config['mencoder']),"-dvd", str(self.track['id']), "-alang", self.aLanguage, \
  "-sws", "2", "-oac", "copy", "-ovc", ovc, ovc_opts_type, "-vop", vop, "-zoom", "-xy", resolution, \
                "-o", self.output, "2>/dev/null"]
                
                if int(self.config['aspectratio']) is not 0:
                    video_pass.insert(3, "-aspect")
                    video_pass.insert(4, self.aro[self.config['aspectratio']])

                if self.sLanguage is not "None":
                    video_pass.insert(3, "-slang")
                    video_pass.insert(4, self.sLanguage)

#                 # Uncomment to test command
#                 string1 = ""
#                 string2 = ""
#                 for bit in audio_pass:
#                     bit = "".join([" ", str(bit)])
#                     string1 = "".join([string1, bit])
#                 for bit in video_pass:
#                     bit = "".join([" ", str(bit)])
#                     string2 = "".join([string2, bit])
#                 print string1
#                 print string2
#               sys.exit(1)

                self.runPass("audio", audio_pass)
                self.runPass("video1", video_pass)

                os.popen("rm divx2pass.log 2>/dev/null")
                os.popen("".join(["rm ", self.outdir, "frameno.avi 2>/dev/null"]))


            elif self.config['passes'] is 3:
                audio_pass = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-oac",  "mp3lame", "-lameopts", lameopts, "-ovc", "frameno", "-o", \
                "".join([self.outdir, "frameno.avi"]), "2>/dev/null"]
  
  video_pass1 = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-sws", "2", "-oac", "copy", "-ovc", ovc, ovc_opts_type, "".join([ovc_opts, ":vpass=1"]), "-vop", vop, \
                "-zoom", "-xy", resolution, "-o", self.output, "2>/dev/null"]
  
                video_pass2 = [str(self.config['mencoder']), "-dvd", str(self.track['id']), "-alang", self.aLanguage, \
                "-sws", "2", "-oac", "copy", "-ovc", ovc, ovc_opts_type, "".join([ovc_opts, ":vpass=2"]), "-vop", vop, \
                "-zoom", "-xy", resolution, "-o", self.output, "2>/dev/null"]
  
########## To here????##########################    
                if int(self.config['aspectratio']) is not 0:
                    video_pass1.insert(3, "-aspect")
                    video_pass1.insert(4, self.aro[self.config['aspectratio']])
                    video_pass2.insert(3, "-aspect")
                    video_pass2.insert(4, self.aro[self.config['aspectratio']])

                if self.sLanguage is not "None":
                    video_pass1.insert(3, "-slang")
                    video_pass1.insert(4, self.sLanguage)
                    video_pass2.insert(3, "-slang")
                    video_pass2.insert(4, self.sLanguage)

                self.runPass("audio", audio_pass)
                self.runPass("video1", video_pass1)
                self.runPass("video2", video_pass2)
                
                os.popen("rm divx2pass.log 2>/dev/null")
                os.popen("".join(["rm ", self.outdir, "frameno.avi 2>/dev/null"]))

        os.chdir(self.cwd)
        self.int_finishRipping()

```

the section that is not working is 

########### text #####################

########## text ######################

thanks[/QUOTE]

What exactly is not working?  What are the symptoms?  Are there error messages, or does something fail to happen that you expect to happen?

---

### Post by Drakx on 2005-09-05
hi

well every thing works fine right up till this point

```

def ripMp3Audio(self, title):
  self.notify_newPass("audio")
		self.state = "ripping"
		# Work out options to send to mencoder
		if not self.config['volumead']:
			vol = "".join([":vol=", str(self.config['volumead'])])
		else:
			vol = ""
		lameopts = "".join(["cbr=", str(title['abr']), str(vol)])
		arguments = ["-dvd", str(title['id']), "-alang", title['alang'], \
			"-oac", "mp3lame", "-lameopts", lameopts, "-ovc", "frameno", "-o", \
			os.path.join(self.config['outputdir'], "frameno.avi")]
		# Run mencoder
		self.run('mencoder', arguments, self.mencodeFinished, self.mencodeProgress, \
			flushbuffer=1, data="audio")
			
	
	def ripVideo(self, title):
		"""Rip the video from a DVD title, and optionally merge with audio"""
		self.notify_newPass("video")
		self.state = "ripping"
		
		# Work out filename
		output = os.path.join(self.config['outputdir'], str(title['name']))
		output = ''.join([output, ".avi"])
		
		## Work out options to send to mencoder
		# PDA?
		if self.config['pdamode'] == 'On':
			resolution = "320"
		else:
			resolution = "720"
		# Audio?
		if self.config['audiocodec'] == 'mp3':
			oac = "copy"
		else:
			oac = "null"
		# Video?
		if self.config['videocodec'] == 'xvid':
			ovc = "xvid"
			ovc_opts_type = "-xvidencopts"
			ovc_opts = "".join(["4mv:me_quality=6:mod_quant:quant_range=1-31/1-31:", \
				"bitrate=", str(int(title['vbr']))])
		else:
			ovc = "lavc"
			ovc_opts_type = "-lavcopts"
			ovc_opts = "".join(["vcodec=mpeg4:vhq:vbitrate=", str(int(title['vbr']))])
		# Cropping
		vop = "".join(["scale,crop=", title['crop']])
		# Deinterlacing?
		if self.config['deinterlacing'] == 'On':
			vop = "".join([vop, ",dint"])
		# Build it all up
		arguments = ["-dvd", str(title['id']), "-alang", title['alang'], "-oac",  oac, \
		"-ovc", ovc, ovc_opts_type, ovc_opts, "-vop", vop, "-zoom", \
		"-xy", resolution, "-o", output]
		# Non-default aspect ratio?
		if self.config['aspectratio'] != 'Default':
			arguments.insert(4, "-aspect")
			arguments.insert(5, self.config['aspectratio'])
		# Subtitles?
		if title['slang'] != 'None':
			arguments.insert(4, "-slang")
   arguments.insert(5, title['slang'])
  # Go for it!
  self.run('mencoder', arguments, self.mencodeFinished, self.mencodeProgress, \
   flushbuffer=1, data="video")

```

that section of code is not ripping the tracks ie video and audio how ever quickrip seems to think it has done its job in 2 secs flat!! here is the cli out put

```

QuickRip will now rip the following tracks:
- Track  1 (/home/drakx/THE_MUMMY_RETURNS_UK-1.avi) at 638kbps
Hit enter to begin ripping, or 'b' to return to the main menu
>


* Ripping title THE_MUMMY_RETURNS_UK-1 (1 of 1)
audio | 100% |============================================================|
video | 100% |============================================================|

* Ripping complete. Hit enter to return to the main menu


```

what is suppose to happen is quickrip is suppose to run mplayer what i mean is this 

```
nice -n 3 mencoder -oac mp3lame -lameopts mode=2:cbr:br=128:vol=0 -ovc frameno -o frameno.avi dvd://1
```

for mp3 audio ripping and video some thing like this
```

nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=657:vhq:vpass=1 \
 -ffourcc XVID   dvd://1 -o /dev/null
```

also

```

nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=657:vhq:vpass=2 \
 -ffourcc XVID   dvd://1 -o "movie.avi
```

ive run these commands in a terminal and they work how ever when i try to put them commands into quickrip, it thinks its that quick it can do a 2 hour in 2 secs flat (timed) and there is nothing produced no video/audio :-|   ](*,) 

any ideas you can provid will be great

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=Drakx]hi
ive run these commands in a terminal and they work how ever when i try to put them commands into quickrip, it thinks its that quick it can do a 2 hour in 2 secs flat (timed) and there is nothing produced no video/audio :-|   ](*,) 

any ideas you can provid will be great[/QUOTE]
Well, have you tried just printing out the command lines the program thinks it's executing?  That way you can compare it with the commands you would normally type in so you can see what is going wrong.

---

### Post by Drakx on 2005-09-06
this the command quickrip runs to rip audio

```
lameopts = "".join(["cbr=", str(title['abr']), str(vol)])
                arguments = ["-dvd", str(title['id']), "-alang", title['alang'], \
                        "-oac", "mp3lame", "-lameopts", lameopts, "-ovc", "frameno", "-o", \
                        os.path.join(self.config['outputdir'], "frameno.avi")]
                # Run mencoder
                self.run('mencoder', arguments, self.mencodeFinished, self.mencodeProgress, \
                        flushbuffer=1, data="audio")
```

no matter what i do for some strange reason just wont run i know that
```
nice -n 3 mencoder dvd://# options
```

is needed in the mplayer pre realeses but even when i try put the above "nice -n 3" section the same thing happens

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=Drakx]this the command quickrip runs to rip audio

```
lameopts = "".join(["cbr=", str(title['abr']), str(vol)])
                arguments = ["-dvd", str(title['id']), "-alang", title['alang'], \
                        "-oac", "mp3lame", "-lameopts", lameopts, "-ovc", "frameno", "-o", \
                        os.path.join(self.config['outputdir'], "frameno.avi")]
                # Run mencoder
                self.run('mencoder', arguments, self.mencodeFinished, self.mencodeProgress, \
                        flushbuffer=1, data="audio")
```

no matter what i do for some strange reason just wont run i know that
```
nice -n 3 mencoder dvd://# options
```

is needed in the mplayer pre realeses but even when i try put the above "nice -n 3" section the same thing happens[/QUOTE]

Sorry, I guess I wasn't as clear as I could have been.  I don't have the whole program in front of me, so I can't see what the self.run() method is doing.  I meant, if you drill down far enough, the program must be doing an os.system() or a popen() type of call to interact with the operating system.  My suggestion was that you put diagnostic code at this point and print out the exact command line after all the string mangling has been done.  Then you can consider scenarios like: Is a relative command line being used?  If so, what is my current working directory?  Is a return status coming back?  If so, what is it?

---

