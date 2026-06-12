---
title: "Scripting examples --&gt; a real timesaver"
date: 2013-05-26
forum: Programming Talk
---

### Post by texaswriter on 2013-05-26
Not asking any question here, just posting a recent script I came up with to save myself some time. Having started using Linux in 2010, I merely started using it because Vista was very unreliable and buggy for my routine document editing and extensive file copying that I did to keep my USB disc in sync with my school laptop in sync with my home computer in sync with my backup drive. Since I worked ft and went to school ft, I really didn't have time to be bothered by Vista's bugs or really learning too much about Linux. I picked up with Debian, then later Ubuntu, and have been picking things up as I go to make my computing life easier. 

So using BASH scripts or even one liners in a BASH shell was a learning curve for me. At first I struggled with learning a subset of commands that would be useful, then I practiced with piping in its various forms where this proved useful, and even learning to use variables, string search/replacement, and for loops. Since I really only expanded my repertoire out of necessity and not really idle curiosity, my growth has been slow. Here are a few examples of my more complicated one-liner scripts that have saved me a great deal of time.

Although I have lost the original script (wouldn't take long to figure it out), I once had a school project that required separate image streams for processing, specifically the depth map image and the rgb image from a kinect sensor. These image streams would be fed to separate image processing scripts. Many pictures were taken (several thousand) to develop and test the routines. It would have taken countless hours (maybe hundreds) to separate each image into the separate bitmap. Needless to say, a simple script with imagemagick backend was able to separate each image into its separate depth map and rgb image and copy them to their respective folders. It took me about 30 minutes to research how to do this, a few minutes to perfect the one-liner, and some ~20 minutes to process the images, but it saved me hundreds of hours and the deadline. 

Most recently, I put any pictures I take on a trip into a folder (in the directory below, 20130520-Hiking is the folder). For simplicity, I copy all the raw files into a subfolder of the main trip folder. Then, I go through the pictures in this folder and sort them into sub-folders according to subject or composition. Needless to say, I typically end up with 15-20 separate "subjects". I sort them into folders myself. To avoid spending twice this time creating an additional folder in each sub-folder and copying the raw files into each file, I made this script to search the current "subject" sub-folder and  move the appropriate raw files into a sub-sub-folder. Saves me roughly 10 minutes each trip compared to the 30 seconds to type this script up and the 1 minute to execute it 15 times. cd 01[tab][type script here][enter]cd ..[enter]cd 02[tab][up arrow][up arrow][up arrow][enter]  ... rinse, repeat. Of course I could have automated the directory traversal and recursion as well, but that would have been more trouble than it was worth.

```
mkdir 01\ -\ RAW; for file in *.JPG; do echo "$file"; mv ~/Pictures/2013/20130520-Hiking/01\ -\ RAW/${file/.JPG/.NEF} 01\ -\ RAW/${file/.JPG/.NEF}; done
```

TLDR; Needless to say, although I have never tried to be a master at scripting or the Linux terminal, and despite still not being a master/expert, I have been able to put it to very good use. I will continue to learn and apply this to my computing lifestyle. Anybody else should consider that their time is too valuable to waste, so consider that as a part of the Linux lesson. I waste very little time using Linux and accomplish pretty much exactly what I expect. The same cannot be said of other computing environments that I have to use...

---

