---
title: "usbkbd.c help understanding ubb_kbd_irg(struct urb *urb)"
date: 2010-11-20
forum: Programming Talk
---

### Post by cpsusie on 2010-11-20
For a class project, I have been attempting to dissect this usb keyboard driver.  While I think I have a pretty good (at least general) idea of what is going in most places, I have been agonizing over this particular method for weeks.  Please understand that I and my group mates have VERY little experience writing anything other than business applications using things like C# and Java -- so this sort of thing is a whole new monster to us.

Let me post the function that is agonizing me so much and making me simply want to die die die die die (LOL). 

```
static void usb_kbd_irq(struct urb *urb)
{
    struct usb_kbd *kbd = urb->context;
    int i;

    switch (urb->status) {
    case 0:            /* success */
        break;
    case -ECONNRESET:    /* unlink */
    case -ENOENT:
    case -ESHUTDOWN:
        return;
    /* -EPIPE:  should clear the halt */
    default:        /* error */
        goto resubmit;
    }

    for (i = 0; i < 8; i++)
        input_report_key(kbd->dev, usb_kbd_keycode[i + 224], (kbd->new[0] >> i) & 1);

    for (i = 2; i < 8; i++) {

        if (kbd->old[i] > 3 && memscan(kbd->new + 2, kbd->old[i], 6) == kbd->new + 8) {
            if (usb_kbd_keycode[kbd->old[i]])
                input_report_key(kbd->dev, usb_kbd_keycode[kbd->old[i]], 0);
            else
                dev_info(&urb->dev->dev,
                        "Unknown key (scancode %#x) released.\n", kbd->old[i]);
        }

        if (kbd->new[i] > 3 && memscan(kbd->old + 2, kbd->new[i], 6) == kbd->old + 8) {
            if (usb_kbd_keycode[kbd->new[i]])
                input_report_key(kbd->dev, usb_kbd_keycode[kbd->new[i]], 1);
            else
                dev_info(&urb->dev->dev,
                        "Unknown key (scancode %#x) released.\n", kbd->new[i]);
        }
    }

    input_sync(kbd->dev);

    memcpy(kbd->old, kbd->new, 8);

resubmit:
    i = usb_submit_urb (urb, GFP_ATOMIC);
    if (i)
        err_hid ("can't resubmit intr, %s-%s/input0, status %d",
                kbd->usbdev->bus->bus_name,
                kbd->usbdev->devpath, i);
}

static int usb_kbd_event(struct input_dev *dev, unsigned int type,
             unsigned int code, int value)
{
    struct usb_kbd *kbd = input_get_drvdata(dev);

    if (type != EV_LED)
        return -1;

    kbd->newleds = (!!test_bit(LED_KANA,    dev->led) << 3) | (!!test_bit(LED_COMPOSE, dev->led) << 3) |
               (!!test_bit(LED_SCROLLL, dev->led) << 2) | (!!test_bit(LED_CAPSL,   dev->led) << 1) |
               (!!test_bit(LED_NUML,    dev->led));

    if (kbd->led->status == -EINPROGRESS)
        return 0;

    if (*(kbd->leds) == kbd->newleds)
        return 0;

    *(kbd->leds) = kbd->newleds;
    kbd->led->dev = kbd->usbdev;
    if (usb_submit_urb(kbd->led, GFP_ATOMIC))
        err_hid("usb_submit_urb(leds) failed");

    return 0;
}
```

I understanding that this translates the information received from the usb keyboard (scancodes?) into keycodes that the kernel can use.  I really don't get the mechanics of it.  I've read a whole lot on usb and linux and can't find anything that describes exactly what is going on here.  In particular, I find the for loops (why does it need 8 chars? -- what is the purpose of the 224 offset, what the hell does that >> bitwise shift do?  

Can someone please break this down in crayon or as close to crayon as your time and generosity will allow?  I think I can get the rest of this driver or well enough for my class but this section is just impossibly difficult.

Thank you.

Chris

---

### Post by vl012 on 2012-04-05
Good evening!

Well, I have the following explanation.
It is based on my investigation of the topic and can contain mistakes.

> what is the purpose of the 224 offset

I can guess about the origins of the 224 number.
Take a look at the "usb_kbd_keycode" array (http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/drivers/hid/usbhid/usbkbd.c#L48).
 It has 256 members. The first 4 are not used as the keycodes. Keycodes, starting from value 29 are for non-printable characters (Ctrl, Alt, etc). So, we have 224 keycodes left.

> why does it need 8 chars

A keycode is stored in a byte. 
">>" makes it possible to move inside a byte and apply "& 1" operation to bits (one by one).
See also http://www.cs.umd.edu/class/sum2003/cmsc311/Notes/BitOp/bitwise.html.

The usage of "kbd->new" construction can be explained by the fact that 
"The USB keyboard driver pipes scancodes into the normal kernel keyboard driver."
(see http://www.linux-usb.org/USB-guide/x699.html).

Of course my explanation does not show the complete picture of what is going on.
But I hope it can help some people to understand the discussed code better.

Good luck!
Vladimir

---

