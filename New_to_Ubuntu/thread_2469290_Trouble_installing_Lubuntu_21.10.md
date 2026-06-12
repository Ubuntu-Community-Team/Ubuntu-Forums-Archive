---
title: "Trouble installing Lubuntu 21.10"
date: 2021-11-24
forum: New to Ubuntu
---

### Post by nginmu on 2021-11-24
Lubuntu 21.10

Downloaded the AMD64 iso from [https://lubuntu.me](https://lubuntu.me) & checked the sha256 hash

Used startup disk creator to create bootable USB memory stick

Tried to install on HP G72 laptop (8Gb RAM, core i3 M220, 10 years old?) which previously ran 20.04 fine

Grub loaded & gave options, lubuntu, lubuntu safe graphics, memory test

Both lubuntu options just stalled with blank screen & rapidly flashing light on usb stick.

Memory test option (memtest86?) showed many, many errors (constant stream, like everything it was testing was throwing an error, screen very red!)

Tried removing one of two 4Gb RAM sticks - errors went away.

Tried all combinations of RAM in the two slots. No errors as long as only one RAM stick installed at a time.

Removed USB, replaced both RAM sticks, used BIOS' own memory test facility. No errors.

Windows boots & runs fine.

Tried installing Impish with only one 4Gb RAM stick installed. No memory errors, but still no install, just sits at blank screen, USB flashing

Tried resetting BIOS defaults, no secure boot option visible, still no joy

Tried going back to 20.04.3 - installed fine (although memtest86 did lock up when I tried it)

Am I missing something obvious or is my hardware now just too old..

---

### Post by guiverc on 2021-11-24
Personally I would boot the *live* media on another box and see how it performs there.  My suspicion from your description with RAM errors is either

- faulty hardware; as shown by RAM test errors
- faulty write to install media ; the flashing USB icon maybe the system validating that; but the screen being blank didn't show errors that would have told you the media was flawed; did you switch to text terminal and explore there?

In my experience about 5-8% of ISO writes to thumb-drive media fail; and that's using sandisk media (it's worse with other brands), but I'm writing ISOs to media *daily* and thus see the issues somewhat regularly.  Booting it in another box (I'd likely use two, one of the same or similar type & one of a different type, where type is uEFI, Secure uEFI, BIOS..)  If the media works on the other box(es), then I'd assume it's a box specific issue..

Assuming it's a box specific issue (*end of last paragraph*), you didn't say if the 20.04 you say worked was using the GA or HWE kernel stack; either way it was likely 5.4 (GA) or 5.11 (for HWE with 20.04.3) and not 20.04.4 (5.13) or the 21.10 kernel stack being a later stack - thus it maybe kernel related. I won't continue with what I'd do here, as I'd be *checking*  write of ISO to media first, or your hardware/RAM first

---

