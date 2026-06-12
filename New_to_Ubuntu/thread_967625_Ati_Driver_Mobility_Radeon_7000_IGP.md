---
title: "Ati Driver Mobility Radeon 7000 IGP"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by naesin on 2008-11-02
Hi,

Newbie to the linux world, but getting along quite well. Just wondering how i would go about checking for the latest drivers for my graphics card. Running lshw, tells me 

          description: Host bridge
          product: R200 AGP Bridge [Mobility Radeon 7000 IGP]
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64 module=ati_agp

how do i go about checking for updates?

Naesin

---

### Post by Daveth on 2008-11-02
you would use envyng.
You can find this in the repository- go system/admin/synaptic package manager, and search for this and add it to your system.
You will need your root password for this- the one you created.
This homepage gives some background to it

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I always like to purge old drivers and then add new ones.I have not loaded up Intrepid myself so trust is is the same as hardy in this respect.
An alternative is to use the restricted drivers option available within ubuntu - depends how new/stable/unstable you want it to be.

---

### Post by overdrank on 2008-11-02
> **naesin said:**
> Hi,

Newbie to the linux world, but getting along quite well. Just wondering how i would go about checking for the latest drivers for my graphics card. Running lshw, tells me 

          description: Host bridge
          product: R200 AGP Bridge [Mobility Radeon 7000 IGP]
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64 module=ati_agp

how do i go about checking for updates?

Naesin

Hi and welcome, ATI has dropped support for cards older than 9500 I believe and the driver installed with Ubuntu ( Hardy 8.04 for sure) works great and I have one with the desktop effects working. :)
Edit to slow, And I believe Envy does not support as well. Please correct me if I am mistaken.

---

### Post by overdrank on 2008-11-02
> **naesin said:**
> Hi,

Newbie to the linux world, but getting along quite well. Just wondering how i would go about checking for the latest drivers for my graphics card. Running lshw, tells me 

          description: Host bridge
          product: R200 AGP Bridge [Mobility Radeon 7000 IGP]
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64 module=ati_agp

how do i go about checking for updates?

Naesin

Hi and welcome, ATI has dropped support for cards older than 9500 I believe and the driver installed with Ubuntu ( Hardy 8.04 for sure) works great and I have one with the desktop effects working. :)
Edit to slow. 
And I believe Envy does not support as well.

---

### Post by Daveth on 2008-11-02
ah, good point Overdrank- I did not really take in the card type, beyond ATI. There used to be a list of cards supported under Legacy Envy (as opposed to EnvyNG), but I have no idea if you can run the legacy Envy on newer Unbuntu's.
In which case you are a bit stuck with what you have got. But is is nearly Christmas.....

---

