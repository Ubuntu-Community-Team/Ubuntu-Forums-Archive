---
title: "F-Spot help"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by anokienurse on 2013-03-15
I have tried to import pictures from my digital camera (a Nikon), it comes on and shows only one picture but does show that it is importing all the ones on my camera when I click "Import" but they never show up in my F-Spot picture file.  I pick "Choose Import Source"- Nikon, it shows one of the pictures that is in the camera. In the section Detect Duplicates it is checked, Include subfolders is checked but Copy files to the Photos folder is not checked.  Do I need to check that box (only when importing from my camera?) to insure that they show up but my son told me that it shouldn't be checked because it would add too many extra GB's to my harddrive as it was copying my whole picture folder again, and I originally had to delete the "Photo" folder as I crashed F-Spot (and just about crashed my whole computer) as well as delete the hidden folders that my son told me to do and then restart it and start again.  Also is there a way to only import certain pictures?  I keep many on my camera that I have already downloaded into my picture file when I had my Mac and don't want them in my picture file again.  I use F-Spot  because it gives me more functionality and a way to actually identify the people in a picture which Shotwell did not.  I had been using Picasa when I had my Mac but it was very unstable on Linux and crashed, with Picasa I had a folder for each person and I could add all of the pictures that they were into thier own folder,  I couldn't do any of that with Shotwell but could at least place them in something somewhat similiar on F-Spot.  I sure hope you can help with my questions.  Thank you.

---

### Post by sully101 on 2013-03-16
I havn't used F-spot but you may find your answer here [http://f-spot.org/Main_Page]("http://f-spot.org/Main_Page"). You should be able to import only the pictures you want and you probably will have to check that box if you want them coppied to your hard drive. Roughly how many pictures are on your camera? If there are alot it may just be taking a long time to index them and check for duplicates. You can check how much room you have on the harddrive by doing ```
df -h
``` from the terminal or by opening "System Monitor" and clicking on the "File Systems" tab. As a side note Shotwell does seem to support tags is that the way that you are identifying people in the photo? Hope some of this helps but I pretty much use Shotwell.

---

### Post by anokienurse on 2013-03-18
> **sully101 said:**
> I havn't used F-spot but you may find your answer here [http://f-spot.org/Main_Page](http://f-spot.org/Main_Page). You should be able to import only the pictures you want and you probably will have to check that box if you want them coppied to your hard drive. Roughly how many pictures are on your camera? If there are alot it may just be taking a long time to index them and check for duplicates. You can check how much room you have on the harddrive by doing ```
df -h
``` from the terminal or by opening "System Monitor" and clicking on the "File Systems" tab. As a side note Shotwell does seem to support tags is that the way that you are identifying people in the photo? Hope some of this helps but I pretty much use Shotwell.

With F-Spot there is a place under the picture itself that I can identify who is in the picture as well as tagging it with a name so that I can then click on that name and see all of the pictures that are under that name.  Shotwell didn't seem to have that feature of having a place under the picture to identify who is who.  I also wasn't able to see how I could "tag" them under something other than where Shotwell had them.  If that is incorrect than please enlighten me as to how I can do both of these features which are closer to Picasa that I was used to.  I had also tried to "Import" thru Shotwell with the same result (probably need to check that box for the import), they never showed up in my picture folder so that I could then access them and place copies in my genealogy program.  I also have another question, I couldn't figure out how to email them thru either F-Spot or Shotwell?  It was so easy with Picasa, I just found the file I wanted clicked on it and down at the bottom it would hold what ever picture you placed in the box and then you clicked "email" you added you address and hit send.  I tried to do figure out how to do it thru F-Spot and had so much difficulty I just found the pictures I wanted in my picture folder, attached them directly in my email  and sent them that way but that is cumbersome as Picasa automatically compressed them for emailing and if it is a large picture I have to make it smaller myself before I send it.  

I do have about 90 pictures on my camera (makes it convienent to show a small version of pictures to family but when I tried to import them it only showed one and didn't give me a choice on which ones that I wanted to import, it only gave me the choice of "all" or import the one showing.  To have to import one at a time is very time consuming and it still only showed the very first one on my camera.  Guess I will have to just have a folder backup with everything on my camera and then delete some off of it.  Jean

---

### Post by sully101 on 2013-03-18
Hi Jean,

With Shotwell you would have to create a tag for each persons name but I dont think it would identify who is who inside the photo, just that they are in the photo :( I have attached a screen shot of my Shotwell with some photos tagged, (I dont really use that feature) hope it helps. Shotwell will publish photos too and email+zip them. I just tried f-spot and got the same behavior with only one picture showing when I tried to import a folder :(

Shotwell preferences has a checkbox for "raw developer" you may get better luck by changing this and then reconnecting your camera. I have noticed also that my camera has several settings to do with how it exports the photos, I have mine set so I can just browse it like a usb stick and then copy and paste the pictures into my "/home/Pictures" folder with nautilus.

screen shot[IMG]http://ubuntuone.com/6zgDM8RgqRFMiJZEF9i3Ri[/IMG]

Sorry I'm not much help. Let me know how things go, I would be interested to see how you get on. If you do get the import working you can just select the ones you want by holding down the [ctrl] key and clicking the pictures that you want.

---

### Post by Spacecoaster on 2013-03-20
anokienurse: Sorry, I can't offer assistance, just moral support.  I've had the same problem with my Nikon camera (D3100) and f-spot since I upgraded to ubuntu 12.04.  It worked fine in 10.04 so not doubt there is some subtlety that I have missed following the upgrade.    

I don't find shotwell as useful as f-spot, either. But at least shotwell works and I can import my photos using it.  If I find a solution that might help you to get f-spot working then I'll let you know.

Regards,

---

