---
title: "SDL_JoystickGetAxis doesn't return a correct value"
date: 2009-11-26
forum: Programming Talk
---

### Post by 0xABC123 on 2009-11-26
I have an old xbox gamepad. It has 2 joysticks (2 axis per joystick), a d-pad, 2 triggers and some buttons.

For some odd reason, SDL_JoystickGetAxis() always returns positive value, no matter if the real value is negative or positive.

jscalibrator shows correct values, negative when the joystick points at left and positive when it points at right, so the problem is not in my xbox gamepad.

What am I doing wrong?

---

### Post by 0xABC123 on 2009-11-26
The problem seems to be here:
```

static int get_joystick_axis( int js, int axis )
{
    Sint16 raw;
    
    ASSERT_JOYSTICK_NUM( js );
    raw = SDL_JoystickGetAxis( joysticks[js], axis );
    
    printf( "%d\n", raw ); // raw is correctly something between -32767 and +32767
[COLOR=Red] _   int tmp = (signed int) raw; // conversion fails and tmp is something between 0 and 65404_[/COLOR]
    
    return tmp;
}

```int is 4 bytes and Sint16 is 2 bytes. Why the conversion messes it up?

EDIT: Solution: ```

static int get_joystick_axis( int js, int axis )
{
    Sint16 raw;
    
    ASSERT_JOYSTICK_NUM( js );
    raw = SDL_JoystickGetAxis( joysticks[js], axis );
    
    int tmp = (int) raw;
    
    if ( tmp > 32767 )
    {
        tmp -= 32767;
        tmp = ( 32767 - tmp ) * -1;
    }
    
    return tmp;
} 
```**This works but how/why does it work?**

---

