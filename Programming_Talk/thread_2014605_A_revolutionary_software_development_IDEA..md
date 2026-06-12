---
title: "A revolutionary software development IDEA."
date: 2012-07-02
forum: Programming Talk
---

### Post by callmemahavir on 2012-07-02
Usually software are developed in 2 phases. One is library and your software. Mostly libraries are developed by third party.

A new idea is that software development can be put into 3 stages.

1. Designing and publishing interfaces.
2. Doing the library with published interfaces.
3. Your software.

The Advantages are...

1. You do not have to rewrite how the string interface again. so that common on all platform.

2. Because you have to study interfaces to work with the library. So that learning one interface is enough to work on all platform.

3. Because interface is standardized your code need not be changed to work in different platform.

4. With single interface all the implementation can be implemented. Which is easy to learn and implement.

5. An example is that consider a service that play sound files.

class SoundPlayerService
{
public:
 virtual PlaySound(char* filename)=0;  
};

So above we have defined the interface.

Lets do some implementation

class mp3player : SoundPlayerService
{
public:
 virtual PlaySound(char* filename)
 {
  /* implementation specific to mp3 playing interface.
 }
}

class wavplayer : SoundPlayerService
{
 virtual PlaySound(char* filename)
 {
  /* implementation specific to mp3 playing interface.
  } 
}

Here write a factory method to get the interface ...

SoundPlayerService* GetWavPlayer()
{
 return (SoundPlayerService*)(new wavplayer());
}

SoundPlayerService* GetMp3Player()
{
 return (SoundPlayerService*)(new mp3player());
}

6. Here naming can be done very easily (GUID or UUID not needed.).

example ...

VendorName.InterfaceName

Here VendorName is vendor whom publishing the interface.
Here InterfaceName in name of the interface published by vendor.

7. Naming of implementation can be done by...

VendorName1.InterfaceName.VendorName2.ImplementationName

Here VendorName2 is implementer of interface and ImplemenataionName is implementation name.

8. The above interface and implementation names can be registered and should be loaded when necessary and return the interface pointer.

With Regards,
Mahavir .D

---

### Post by Tony Flury on 2012-07-02
Sorry to pour water on your parade, but this is not really that revolutionary - attempts have been and are regularly made to define standard interfaces to which them all implementations comply: See the POSIX standards for instance, GTK toolkit (same interface across all platforms), C and Python Standard libraries and the list goes on.

I would also disagree with your premise - often the first stage of any design is to identify the object model, or the common modules requied, and to write the interfaces first, and then add code underneath.

There are a few problems that i can see, that exist with all standad library definitions.

1) Proprietary extensions. All vendors will want to do something beyond the standard interface - so your interface will need to be extended regularly - or become obsolete.

2) S/W paradigms : The POSIX example is a good pointer here. The posix interface definitionns wok great when all you are doing is simple system things, in a procedural type language, but aren't as nice when dealing with OOP for instance - for instance thee is no "file or process as an object" interface that would fit with the OOP paradign.

3) Underlying technology : For instance when you deal with files using the POSIX interfaces, the file dates on Windows mean different things to the file dates on Unix, so you have to be flexible in your code anyway. Your sound card might be able to play 5:1 sounds and mix 3 different inputs. Mine might not - can your interface deal with both situations nicely ?

One big problem i can see with your system is that you actually make you standard library interface vendor specific, by including the vendor in the naming convention. When I write an application I want call some code to play a sound file, I would rather not care which vendor wrote the library, or in some case whether the file is a wav or an mp3 - i just want to play it, the code below the interface should be worying about the type of file, how it is encoded, how loud to play it, and what type of sound card i have.

---

