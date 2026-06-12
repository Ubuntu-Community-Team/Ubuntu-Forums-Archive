---
title: "Code Obsfucation for Java"
date: 2009-07-16
forum: Programming Talk
---

### Post by shatterblast on 2009-07-16
As just something I do in spare time, I have been developing a project for entertainment.  I thought a side benefit might extend to simulations.  I'm not mainly interested in protecting my code, but rather, I prefer to provide protection for some of my artistic digital works.  I am aware that no protection is ever guaranteed.

ProGuard, yGuard (apparently a derivative of RetroGuard), JoGa, JODE, and Jarg seem like open source solutions as far as code protection.  I tried ProGuard at least, and it seems to have problems with the OpenGL-related libraries I import.  yGuard looks interesting, but I need to learn more about Ant scripting.

I haven't decided how to protect my art yet.  I figured some kind of encryption could do the job and just decrypt in a user's memory space.  Maybe I could do something weird like decrypting in an encrypted space so it would be like layers of encryption.  I imagine that would defeat performance.

I originally intended on releasing my things in a LGPL license, which contradicts a user's "freedom."  I want to keep it cost-free at least while learning about how to promote my own freedoms with distributing a software.  Also, I need to respect a couple of the library licenses.

Thanks.

---

### Post by Simian Man on 2009-07-16
All of the obfuscation systems I know only operate on code, not assets so you're kind of looking for the wrong thing.

Just copyright your art (which is automatic anyway).  And if you want, use a simple xor encryption on your art file which will be enough to deter most people.  If your art is desirable enough, someone *will* get it.  If it isn't nobody will care, so you're wasting your time either way.

---

### Post by Zugzwang on 2009-07-16
So what kind of art is it? If we are talking about still images, you can prevent nobody from just taking screenshots of it, so your multi-encryption layers might actually be overkill.

---

### Post by smartbei on 2009-07-16
There is a problem with trying to protect art - It has to be viewed. Anyone will be able to just take a screenshot while your art is displayed, and they have succeeded in copying your artwork.

If you want the files to work only with your program, then encrypting them would work, but keep in mind that since the program can decrypt the files, the key must be in the program, and it could be decompiled to get it.

---

### Post by soltanis on 2009-07-16
Yeah whoa yeah what are you talking about exactly? If art = code then sure those tools work great for obfuscating stuff, if art = pictures, music, or videos...man, you're going to have a tough time -- not even the jackasses at Sony BMG have succeeded in this regard.

---

### Post by az on 2009-07-16
I suggest you look into Creative Commons rather than DRM when dealing with creative works.  

And as for your code, if the lGPL does not suit your purpose, chose another license.  No one is putting a gun to your head to make you use one particular license.

---

### Post by shatterblast on 2009-07-16
> **Simian Man said:**
> All of the obfuscation systems I know only operate on code, not assets so you're kind of looking for the wrong thing.

I only really want obsfucation to hide the I/O values to some extent.  The encryption I can delay on because I'm only releasing software to a few people.  Sharing pieces of the code doesn't bother me since I like helping anyhow.

> **Simian Man said:**
> 
Just copyright your art (which is automatic anyway).  And if you want, use a simple xor encryption on your art file which will be enough to deter most people.  If your art is desirable enough, someone *will* get it.  If it isn't nobody will care, so you're wasting your time either way.

I've done the copyright thing before.  It's not an efficient enough protection for what I'm moving into as an art form.  I figure I can mix the sculpting abilities of polygons from ZBrush or Blender with the life-like resemblances of NURBS from Blender again or possibly Cinema 4D.  Character animations and the like from people to plants come to mind.

And as mentioned before, "I am aware that no protection is ever guaranteed."

---

### Post by shatterblast on 2009-07-16
> **Zugzwang said:**
> So what kind of art is it? If we are talking about still images, you can prevent nobody from just taking screenshots of it, so your multi-encryption layers might actually be overkill.

It's a mix of 2D and 3D.  As far as 2D, I plan on the PNG format that I heavily use at the moment.  Screen-shots might be fine.  It's just the numeric data representing objects that I'm wanting encryption for.  I haven't even searched for a library to do that with yet since I'm focusing more on the code presently.

> **smartbei said:**
> There is a problem with trying to protect art - It has to be viewed. Anyone will be able to just take a screenshot while your art is displayed, and they have succeeded in copying your artwork.

If you want the files to work only with your program, then encrypting them would work, but keep in mind that since the program can decrypt the files, the key must be in the program, and it could be decompiled to get it.

Online financial transactions have been done with 128-bit encryption or higher with credit cards and such.  I was reading into the use of a thin client over a thick client potentially, but that gets deep into the process I think.  The only software I've heard of using it in a related manner has been the Steam technology, which had usage rights for older versions sold to one or two other businesses.  Still, I'm not planning some kind of MMORPG.  That would be silliness.

> **soltanis said:**
> Yeah whoa yeah what are you talking about exactly? If art = code then sure those tools work great for obfuscating stuff, if art = pictures, music, or videos...man, you're going to have a tough time -- not even the jackasses at Sony BMG have succeeded in this regard.

For joking a bit, I think Sony has a reputation of using the best forms of protection available that are always known by them to be "cracked."  I don't know why.  I'm not reverse-engineering any firmware.

If I get the kind of attention that comes with "cracking," then that could mean something good.  I could potentially market my work.  If not, then I suppose I could focus more time on what I enjoy.

---

### Post by shatterblast on 2009-07-16
> **az said:**
> I suggest you look into Creative Commons rather than DRM when dealing with creative works.

I've done that too, the movement with "copylefting," and I wasn't pleased with the results.  I find it amusing that some art pieces I previously distributed found their ways to some image boards.

> **az said:**
> And as for your code, if the lGPL does not suit your purpose, chose another license.  No one is putting a gun to your head to make you use one particular license.

The LGPL seems compatible with all my other efforts.

---

