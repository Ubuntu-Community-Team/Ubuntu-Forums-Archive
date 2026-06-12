---
title: "HandbrakeCLI"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by destructaball on 2008-05-04
Hi I know this is probably a horrifically simple question to answer but I've checked the internet for a while and I can't find anything that helps. I am trying to install Handbrake so i download the CLI for linux and extract the tarball, then something called "HandbrakeCLI" comes out and there is nothing I can do with it. All it has is the wierd gears icon and I've searched the internet for a while and nothing seems to solve it. Please can someone help me and if possible explain it as simply as possible because I'm a bit new to Ubuntu. thanks in advanced.

---

### Post by Monicker on 2008-05-04
Its a binary executable. I've used it a number of times with no problems.

```
chmod +x HandbrakeCLI
./HandbrakeCLI
```

---

### Post by destructaball on 2008-05-04
When I do the second step I get the error message

Missing input device. Run /home/david/Desktop/HandBrakeCLI --help for syntax.

I think I must be doing something wrong, could you tell me exactly what to write if the extracted file is at:

/home/david/Desktop/HandBrakeCLI
Sorry for being a bit useless at this.

---

### Post by Monicker on 2008-05-04
> **destructaball said:**
> When I do the second step I get the error message

Missing input device. Run /home/david/Desktop/HandBrakeCLI --help for syntax.

I think I must be doing something wrong, could you tell me exactly what to write if the extracted file is at:

/home/david/Desktop/HandBrakeCLI
Sorry for being a bit useless at this.


That means it ran, but you did not tell it what to do.  It has many different options.

You should probably take a look at their documentation:

[http://trac.handbrake.fr/wiki/CLIGuide]("http://trac.handbrake.fr/wiki/CLIGuide")

*Also, remember this is a CLI client.  There is no GUI.*

---

### Post by qamelian on 2008-05-04
> **destructaball said:**
> When I do the second step I get the error message

Missing input device. Run /home/david/Desktop/HandBrakeCLI --help for syntax.

I think I must be doing something wrong, could you tell me exactly what to write if the extracted file is at:

/home/david/Desktop/HandBrakeCLI
Sorry for being a bit useless at this.
The second line has a space where it shouldn't. Try ```
./HandbrakeCLI
```

---

### Post by SlappyPappy on 2008-05-06
That is the program and you should move or copy it to /usr/bin with:

sudo cp HandBrakeCLI /usr/bin/HandBrakeCLI

Then you can run it in terminal with a preset like:

HandBrakeCLI -i /media/cdrom0 -o ~/Videos/movie.avi -e ffmpeg -S 700 -E lame -B 160 -R 48 -f avi -2

You might have to change the /media/cdrom0 to whatever your DVD drive is. It will make a file in your Videos folder. This one is designed to make a file about 700MB in size so it will fit on a CD later. Works great.  :)

---

