---
title: "Sharing MacroPolo - A library for macro operations"
date: 2013-06-17
forum: Programming Talk
---

### Post by hakermania on 2013-06-17
The library MacroPolo was developed because while I was trying to make a GUI to xmacro I kept failing, because X server would crash.

So, I decided to try python, and, though it is not GUI, it provides you with some extra functions like searching places of the screen for a specific point and getting that point etc.

That allows you to do operations like:


[LIST]
[*]Cursor:
[/LIST]

[LIST=1]
[*]Move Cursor
[*]Get Cursor position
[*]Left/Middle/Right click
[/LIST]


[LIST]
[*]Keyboard:
[/LIST]

[LIST=1]
[*]Write raw ascii characters
[*]Simulate Key Down/Key Up
[/LIST]


[LIST]
[*]Pixels of the screen:
[/LIST]

[LIST=1]
[*]Get the color of a pixel of the screen
[*]See if a specific color exists on a region of the screen
[*]Get the total count of pixels that have a specific color on an area
[*]Wait for a pixel color (or multiple colors) to show up on a point (or multiple points)
[*]Wait for a pixel color to show up on an area
[*]Most of the waiting functions above have a "special" version where you can pass a function pointer to be run on your preferred timeout as long as the program is waiting
[*]Save section of the screen to file (takes screenshot of region of the screen, useful when you need to do Optical Character Recognition with some program)
[/LIST]

The library only depends on 
```

python-qt4
python-pyatspi2

```

and I believe it to be well documented. In general, the library is powerful enough to let you do complicated repetitive operations, even if they need to be executed slightly differently each time. Consider the following scenario:

You are playing a game where you have to farm. So, you have a scythe and you have to chop down corn. Each time the corn appears on different place of the screen, but all the corns have a unique color. So, you can search the region of the screen where the game is being played for the color of corn. In every occurrence you will click the corn and chop it down (mention that the functions that wait for a specific color on a region return the coordinates of the screen where the color is found, so you can use that in order to click to that point), automatically. So, the program will work each time for every possible combination of the corn plants. (This is NOT the recommended usage of this library, this is just an example to demonstrate its usage and why it can work well on different occasions).

Tips:

[LIST=1]
[*]Keep in mind that getting the color of pixel through color_of_pixel() function and the cursor position through the get_cursor_pos() function, you can find the color of the pixel that is below your cursor. That way you can find the regions that you have to search for a specific color and other useful stuff for use with the other functions.
[*]There is a variable called "PIXELS_SEARCH_SPEED" and, once you have imported macropolo through "import macropolo", you can access it via macropolo.PIXELS_SEARCH_SPEED and you can modify it. This variable is used on funtions that search regions of the screen. It tells how many pixels to skip after one being checked. Its default value is 1 (this means check every pixel of the region). Setting it to a value of 2 will result to a 2 times faster search of the region, but it will skip a pixel after each pixel that is being searched. This is useful if, e.g. you wait for a large circle of a specific color to appear to the screen. In this case, you don't have to search each pixel, you can may as well skip some, because you can be sure that one of the pixels that will be searched will be part of the large circle.
[*]If you want to type out something that in fact needs to be combination of keys, you have to apply the combination. ~!@#$%^&*()_+ cannot appear in key_down/key_up/keyboard functions. If you want to type ! then you have to call Shift and 1 for key_up and then key_down functions.
[/LIST]

```
#!/usr/bin/env python
from pyatspi import Registry as controller
from pyatspi import (KEY_SYM, KEY_PRESS, KEY_PRESSRELEASE, KEY_RELEASE, MOUSE_ABS)
from PyQt4.QtGui import QPixmap, QApplication, QColor, QImage, QDesktopWidget, QCursor
from PyQt4.QtCore import QPoint, QRect
import sys, time


key_list = ("1", "2", "3", "4", "5", "6", "7", "8", "9", "0", "-", "=", "`", ".", "Esc", "Shift", "Win", "Up", "Down", "Left", "Right", "Ctrl", "Alt", "space", " ", "Return", "A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z", "a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z", "F1", "F2", "F3", "F4", "F5", "F6", "F7", "F8", "F9", "F10", "F11", "F22")
key_codes = (10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 49, 60, 9, 50, 133, 111, 116, 113, 114, 37, 64, 65, 65, 36, 38, 56, 54, 40, 26, 41, 42, 43, 31, 44, 45, 46, 58, 57, 32, 33, 24, 27, 39, 28, 30, 55, 25, 53, 29, 52, 38, 56, 54, 40, 26, 41, 42, 43, 31, 44, 45, 46, 58, 57, 32, 33, 24, 27, 39, 28, 30, 55, 25, 53, 29, 52, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 95, 96)
app=QApplication(sys.argv)


#the bigger the faster (but it skips more pixels). Set to 1 will search all the pixels.
PIXELS_SEARCH_SPEED=1;


def to_upper(string):
    """Returns python or Qt String to upper"""
    try:
        return string.toUpper()
    except:
        return string.upper()


def to_lower(string):
    """Returns python or Qt String to lower"""
    try:
        return string.toLower()
    except:
        return string.lower()
        
def move_cursor_to(x, y):
    """Moves the cursor to the x, y coordinates"""
    controller.generateMouseEvent(x, y, MOUSE_ABS)
    
def get_cursos_pos():
    """Returns the cursor pos as a tuple"""
    return [QCursor.pos().x(), QCursor.pos().y()]


def left_click_to(x, y):
    """Left clicks the cursor to the x, y coordinates"""
    if(x > 0 and y > 0):
        controller.generateMouseEvent(x, y, 'b1c')
        
def middle_click_to(x, y):
    """Middle clicks the cursor to the x, y coordinates"""
    if(x > 0 and y > 0):
        controller.generateMouseEvent(x, y, 'b2c')
        
def right_click_to(x, y):
    """Right clicks the cursor to the x, y coordinates"""
    if(x > 0 and y > 0):
        controller.generateMouseEvent(x, y, 'b3c')


def keyboard(key):
    """
    Types the tuple 'key' to the screen. For example you can say:
    ["Alex was in a bad mood lately", "Return", "A", "B", "1", "2", "comma"] and it will try to print:
    Alex was in a bad mood lately
    AB12,
    A simple string rather than a tuple may as well be passed to this function.
    """
    for i in key:
        if i in key_list:
            controller.generateKeyboardEvent(key_codes[key_list.index(i)], None, KEY_PRESS)
            time.sleep(0.01)
            controller.generateKeyboardEvent(key_codes[key_list.index(i)], None, KEY_RELEASE)
        else:
            for j in i:
                if j in key_list:
                    controller.generateKeyboardEvent(key_codes[key_list.index(j)], None, KEY_PRESS)
                    time.sleep(0.01)
                    controller.generateKeyboardEvent(key_codes[key_list.index(j)], None, KEY_RELEASE)
                else:
                    print "Unkown character to be sent as event:", j


def key_down(key):
    """
    This is a more specific function than keyboard(). It can send specific
    key-pressed events, in case you want to do keyboard combinations, like Alt+F4
    The argument can only be a string. If you want to send (e.g.) Alt+F4 then you
    should call it as:
    key_down("Alt")
    key_down("F4")
    time.sleep(0.2)
    key_up("Alt")
    key_up("F4")
    """
    if key in key_list:
        controller.generateKeyboardEvent(key_codes[key_list.index(key)], None, KEY_PRESS)


def key_up(key):
    """
    It releases a pressed key. See the key_down(key) function for more info.
    """
    if key in key_list:
        controller.generateKeyboardEvent(key_codes[key_list.index(key)], None, KEY_RELEASE)


def pixel_color_in_area_counter(rectangle, color):
    """
    Searches the rectangle area 'rectangle' for the color 'color'.
    It returns an integer indicating the times that the 'color'
    was found inside the 'rectangle'.
    The rectangle is a tuple [x, y, width, height], where x, y the
    coordinates of the top left corner and width, height the width
    and the height of the rectangle.
    The color is a string with a hexadecimal representation of 
    a color (e.g. #000000)
    """
    x = rectangle[0]
    y = rectangle[1]
    width = rectangle[2]
    height = rectangle[3]
    color = to_lower(color)
    
    img = QPixmap.grabWindow(QApplication.desktop().winId()).toImage().copy(x, y, width+1, height+1);
    
    counter=cur_y=cur_x=0
    while( cur_y <= height ):
        cur_x=0
        while ( cur_x <= width ):
            cur_color = QColor(img.pixel(QPoint(cur_x, cur_y)))
            if(str(color)==str(cur_color.name())):
                counter+=1
            cur_x+=PIXELS_SEARCH_SPEED
        cur_y+=1
    return counter;


def pixel_color_in_area(rectangle, color):
    """
    Searches the rectangle area 'rectangle' for the color 'color'.
    If the 'color' is found inside 'rectangle' then it returns True
    as first argument and the point where the pixel was found as the 2nd argument
    If nothing is found then it simply returns False.
    The rectangle is a tuple [x, y, width, height], where x, y the
    coordinates of the top left corner and width, height the width
    and the height of the rectangle.
    The color is a string with a hexadecimal representation of 
    a color (e.g. #000000)
    """
    x = rectangle[0]
    y = rectangle[1]
    width = rectangle[2]
    height = rectangle[3]
    color = to_lower(color)
    
    img = QPixmap.grabWindow(QApplication.desktop().winId()).toImage().copy(x, y, width+1, height+1);
    
    cur_y=cur_x=0
    while( cur_y <= height ):
        cur_x=0
        while ( cur_x <= width ):
            cur_color = QColor(img.pixel(QPoint(cur_x, cur_y)))
            if(str(color)==str(cur_color.name())):
                return True, [cur_x+x, cur_y+y]
            cur_x+=PIXELS_SEARCH_SPEED
        cur_y+=1
    return False, [-1, -1]
    


def color_of_pixel(x, y):
    """Returns the pixel color of the pixel at coordinates x, y."""
    c = QColor(QPixmap.grabWindow(QApplication.desktop().winId()).toImage().pixel(x, y))
    return to_upper(str(c.name()))
    
def wait_for_pixel_color(point, color, timeout):
    """
    Waits till the point 'point' is of color 'color', checking
    every 'timeout' milliseconds. Then it simply exits.
    point is a tuple [x, y]
    """
    color=to_upper(color)
    while color_of_pixel(point[0], point[1]) != color:
        time.sleep(timeout/1000.0)


def wait_for_pixel_colors(points_colors, for_all, timeout):
    """
    'points_colors' argument is a Ax2 array, where A is the number of pixels you want to check.
    For example, the following code:
        points_colors = [ [[5, 6], "#FFFFFF"], [[8, 9], "#000000"] ]
        wait_for_pixel_colors(point_colors, False, 5000)
    will check the pixel 5x6 for the color #FFFFFF and the pixel 8x9 for
    the color #000000 checking every 5 seconds. If one of these colors
    is found then the function exits.
    Note that the pixels are checked one by one in the row they are specified.
    Once all pixels have been checked then the function sleeps for
    'timeout' milliseconds before checking the pixels one by one again. If 'for_all'
    if false, then the function exits if one pixel of all specified has the
    according color, but if 'for_all' is true, then all the specified pixels have to
    have their according color.
    Finally, the function returns the index of the pixel specified. In the above
    example, if the pixel 5x6 has the color #FFFFFF then the function will return
    0, but if the pixel 5x6 doesn't have to color #FFFFFF and the pixel 8x9 has
    the color #000000 then the function will return 1. If there were more pixel-color
    inside the array and e.g. the third pixel-color pair was confirmed, then the function
    would return 2 etc. It is meaningless to return the index if 'for_all' is true, thus
    0 is returned if 'for_all' is true.
    """
    if not for_all:
        found = False
        index=0
        while not found:
            index=0
            for pair in points_colors:
                point = pair[0]
                color = pair[1]
                if(color_of_pixel(point[0], point[1]) == color):
                    found = True
                    break
                index+=1
            time.sleep(timeout/1000.0)
        return index
    else:
        while True:
            cur_checked = 0
            for pair in points_colors:
                point = pair[0]
                color = pair[1]
                if(color_of_pixel(point[0], point[1]) == color):
                    cur_checked+=1
                    if(cur_checked==len(points_color)):
                        return 0
                else:
                    break;
            time.sleep(timeout/1000.0)
        
def wait_for_no_pixel_color(point, color, timeout):
    """
    Waits till the point 'point' is not of color 'color', checking
    every 'timeout' milliseconds. Then it simply exits.
    point is a tuple [x, y] while color is a string (e.g. #000000)
    """
    color=to_upper(color)
    while color_of_pixel(point[0], point[1]) == color:
        time.sleep(timeout/1000.0)


def wait_for_pixel_color_in_area(rectangle, color, timeout):
    """
    Waits till the rectangle 'rectangle' contains a pixel of color
    'color', checking every 'timeout' milliseconds. Then it simply
    exits returning the pixel where the color was found first.
    The rectangle is a tuple [x, y, width, height], where x, y the
    coordinates of the top left corner and width, height the width
    and the height of the rectangle.
    The color is a string with a hexadecimal representation of 
    a color (e.g. #000000)
    """
    exists, point = pixel_color_in_area(rectangle, color)
    while not exists:
        time.sleep(timeout/1000.0)
        exists, point = pixel_color_in_area(rectangle, color)
    return point


def wait_for_no_pixel_color_in_area(rectangle, color, timeout):
    """
    Waits till the rectangle 'rectangle' does not contain
    a pixel of color 'color', checking every 'timeout' milliseconds.
    Then it simply exits returning the pixel where the color was found
    first.
    The rectangle is a tuple [x, y, width, height], where x, y the
    coordinates of the top left corner and width, height the width
    and the height of the rectangle.
    The color is a string with a hexadecimal representation of 
    a color (e.g. #000000)
    """
    exists, point = pixel_color_in_area(rectangle, color)
    while exists:
        time.sleep(timeout/1000.0)
        exists, point = pixel_color_in_area(rectangle, color)
    return point


def wait_for_pixel_color_special(function, times, point, color, timeout):
    """
    Waits till the point 'point' is of color 'color', checking
    every 'timeout' milliseconds. It will run the function 'function'
    when it has checked 'times' times for the pixel color (and it
    hasn't found it, otherwise it exits).
    """
    if(times < 1):
        print "Invalid parameter passed for wait_for_pixel_color_special! 'times' should be 1 or more."
        return
    color=to_upper(color)
    times_counter=0
    
    while color_of_pixel(point[0], point[1]) != color:
        times_counter+=1
        if(times==times_counter):
            times_counter=0
            function()
        time.sleep(timeout/1000.0)


def wait_for_no_pixel_color_special(function, times, point, color, timeout):
    """
    Waits till the point 'point' is not of color 'color', checking
    every 'timeout' milliseconds. It will run the function 'function'
    when it has checked 'times' times for the pixel color (and it
    hasn't found it, otherwise it exits).
    """
    if(times < 1):
        print "Invalid parameter passed for wait_for_pixel_color_special! 'times' should be 1 or more."
        return
    color=to_upper(color)
    times_counter=0
    
    while color_of_pixel(point[0], point[1]) == color:
        times_counter+=1
        if(times==times_counter):
            times_counter=0
            function()
        time.sleep(timeout/1000.0)


def wait_for_pixel_color_in_area_special(function, times, rectangle, color, timeout):
    """
    Waits till the rectangle 'rectangle' contains a pixel of color
    'color', checking every 'timeout' milliseconds. It will run the
    function 'function' when it has checked 'times' times for the pixel
    color (and it hasn't found it, otherwise it exits).
    The rectangle is a tuple [x, y, width, height], where x, y the
    coordinates of the top left corner and width, height the width
    and the height of the rectangle.
    The color is a string with a hexadecimal representation of 
    a color (e.g. #000000)
    """
    
    if(times < 1):
        print "Invalid parameter passed for wait_for_pixel_color_in_area_special! 'times' should be 1 or more."
        return
    
    times_counter=0
    
    exists, point = pixel_color_in_area(rectangle, color)
    while not exists:
        times_counter+=1
        if(times_counter==times):
            times_counter=0
            function()
        time.sleep(timeout/1000.0)
        exists, point = pixel_color_in_area(rectangle, color)
        
    return point


def wait_for_no_pixel_color_in_area_special(function, times, rectangle, color, timeout):
    """
    Waits till the rectangle 'rectangle' does not contain
    a pixel of color 'color', checking every 'timeout' milliseconds.
    It will run the function 'function' when it has checked 'times'
    times for the pixel color (and it hasn't found it, otherwise it exits).
    The rectangle is a tuple [x, y, width, height], where x, y the
    coordinates of the top left corner and width, height the width
    and the height of the rectangle.
    The color is a string with a hexadecimal representation of 
    a color (e.g. #000000)
    """
    
    if(times < 1):
        print "Invalid parameter passed for wait_for_pixel_color_in_area_special! 'times' should be 1 or more."
        return
    
    times_counter=0
    
    exists, point = pixel_color_in_area(rectangle, color)
    while exists:
        times_counter+=1
        if(times_counter==times):
            times_counter=0
            function()
        time.sleep(timeout/1000.0)
        exists, point = pixel_color_in_area(rectangle, color)
        
    return point


def save_section_of_the_screen(rectangle, filename):
    """Saves the 'rectangle' in 'filename'.
    The rectangle is a tuple [x, y, width, height], where x, y the
    coordinates of the top left corner and width, height the width
    and the height of the rectangle.
    """
    img=QPixmap.grabWindow(QApplication.desktop().winId()).toImage().copy(QRect(rectangle[0], rectangle[1], rectangle[2], rectangle[3]))
    img.save(filename, "PNG", 100);

```

This library is free to use for any reason and modify without the need to refer to me in any way.

---

