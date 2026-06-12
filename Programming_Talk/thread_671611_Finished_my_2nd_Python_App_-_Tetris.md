---
title: "Finished my 2nd Python App - Tetris"
date: 2008-01-18
forum: Programming Talk
---

### Post by NovaAesa on 2008-01-18
Okay, this morning I just finished my 2nd major python application. It's a basic Tetris clone. I'm interested to get some feedback about what people think of the end user experience as well as what python coders thing about my coding standard/techniques.

To play the game, run main.py.

The controls are pretty simple. Left and right move the piece to the left and right, and up rotates the piece. Down drops the piece by one position and space drops the piece to the bottom. Have fun!

Here's the source:
main.py
[PHP]#!/usr/bin/python

import gtk
import pygtk
pygtk.require("2.0")
import gtk.glade
from tetris import Tetris
import gobject

class TetrisGTK():

    def __init__(self):
    
        #creates widget aliases
        self.wTree = gtk.glade.XML("main.glade")
        self.winMain = self.wTree.get_widget("winMain")
        self.imgMain = self.wTree.get_widget("imgMain")
        self.imgPreview = self.wTree.get_widget("imgPreview")
        self.lblScore = self.wTree.get_widget("lblScore")
        self.lblLevel = self.wTree.get_widget("lblLevel")
        self.lblLines = self.wTree.get_widget("lblLines")
        self.lblEndGame = self.wTree.get_widget("lblEndGame")
        
        #sets up events
        dict ={ "on_winMain_destroy":self.winMain_destroy,
                "on_mnuQuit_activate":self.mnuQuit_activate,
                "on_mnuNew_activate":self.mnuNew_activate,
                "on_winMain_key_press_event":self.winMain_key_press_event }
        self.wTree.signal_autoconnect(dict)
        
        #sets up the first images, which are just blank rectanges or size:
        #320x640 and 128x128.
        xpm_data = ["1 1 1 1",
                     "A c #000000",
                     "A"]
        pixbuf = gtk.gdk.pixbuf_new_from_xpm_data(xpm_data)
        scaled_pixbuf = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, False, 8, 320,
                                                                          640)
        pixbuf.scale(scaled_pixbuf, 0, 0, 320, 640, 0, 0, 320, 640,
                                                        gtk.gdk.INTERP_NEAREST)
        self.imgMain.set_from_pixbuf(scaled_pixbuf)
        scaled_pixbuf = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, False, 8, 128,
                                                                          128)
        pixbuf.scale(scaled_pixbuf, 0, 0, 128, 128, 0, 0, 128, 128,
                                                        gtk.gdk.INTERP_NEAREST)
        self.imgPreview.set_from_pixbuf(scaled_pixbuf)
        
                
    def winMain_destroy(self, widget):
        gtk.main_quit()
        
    def winMain_key_press_event(self, widget, event):
        if event.keyval == gtk.keysyms.Up:
            self.current_game.rotate()
            self.update_display()
        elif event.keyval == gtk.keysyms.Down:
            self.current_game.s_drop()
            self.update_display()
        elif event.keyval == gtk.keysyms.space:
            self.current_game.h_drop()
            self.update_display()
        elif event.keyval == gtk.keysyms.Left:
            self.current_game.sideways('L')
            self.update_display()
        elif event.keyval == gtk.keysyms.Right:
            self.current_game.sideways('R')
            self.update_display()
    
    def mnuQuit_activate(self, widget):
        self.winMain_destroy(self.winMain)
        
    def mnuNew_activate(self, widget):
        self.lblEndGame.set_text("")
        self.current_game = Tetris()
        time_until_next = self.current_game.timer()
        self.timeout_id = gobject.timeout_add(time_until_next,
                                                        self.timeout_callback)
        
    def main(self):
        gtk.main()        
        
    def timeout_callback(self):
        gobject.source_remove(self.timeout_id)
        time_until_next = self.current_game.timer()
        self.update_display()
        if time_until_next != None:
            self.timeout_id = gobject.timeout_add(time_until_next,
                                                        self.timeout_callback)
        else:
            self.lblEndGame.set_text("GAME OVER")
        
    def update_display(self):
        #updates the main image
        pixbuf = self.current_game.get_main_pixbuf(32)
        self.imgMain.set_from_pixbuf(pixbuf)
        #updates the preview image
        pixbuf = self.current_game.get_preview_pixbuf(32)
        self.imgPreview.set_from_pixbuf(pixbuf)
        #updates the score and level
        self.lblScore.set_text("Score: %s" % self.current_game.get_score())
        self.lblLevel.set_text("Level: %s" % self.current_game.get_level())
        self.lblLines.set_text("Lines: %s" % self.current_game.get_lines())

if __name__ == "__main__":
    gui = TetrisGTK()
    gui.main()[/PHP]

tetris.py
[PHP]import random
import gtk

class Tetris(object):

    LINE_VAL = 50
    DROP_VAL = 1
    PIECE_TUPLE = ('Z', 'S', 'T', 'I', 'O', 'L', 'J')

    def __init__(self, width=10, height=20):
        """Creates a new Tetris field.
        
        Parameters: width  - The width of the field. Defaults 10.
                    height - The height of the field. Defaults to 20
        """
        #initialises some instance variables
        self._height = height
        self._width = width
        self._field_square = {}
        self._piece_square = {}
        self._score = 0 #the score
        self._lines = 0 #the number of lines cleared
            
        self._create_next_piece()
        self._create_new_piece()  #Return not val not checked as the first
                                  #piece created should no collide.
        
    def get_main_pixbuf(self, square_size):
        """Creates a pixbuf that represents the current state of the game.
        
        Parameters: square_size - the side length in pixels each square
                                  should be.
        
        Returns: a pixbuf.
        """
        #prepares the image - width, height, num of colours, chr per colour
        first_line = str(self._width) + " " + str(self._height) + " 8 1"
        colour_key = ["  c #000",
                      "Z c #0FF",
                      "S c #0F0",
                      "T c #A00",
                      "I c #F00",
                      "O c #00F",
                      "L c #F0F",
                      "J c #FFF"]
                      
        #creates the image
        picture = []
        square_dict = self._concat_squares()
        for y in range(self._height):
            line = ""
            for x in range(self._width):
                if (x, y) in square_dict.keys():
                    line += square_dict[x, y]
                else:
                    line += " "
            picture.append(line)
            
        #puts the various parts of the image info together
        xpm_data = []
        xpm_data.append(first_line)
        xpm_data.extend(colour_key)
        xpm_data.extend(picture)
        
        #expands the image
        pixbuf = gtk.gdk.pixbuf_new_from_xpm_data(xpm_data)
        width = self._width * square_size
        height = self._height * square_size
        scaled_pixbuf = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, False, 8,
                                                                width, height)
        pixbuf.scale(scaled_pixbuf, 0, 0, width, height, 0, 0, square_size,
                                        square_size, gtk.gdk.INTERP_NEAREST)
        return scaled_pixbuf 
        
    def get_preview_pixbuf(self, square_size):
        """Creates a pixbuf that represents the next piece to be created.
        
        Parameters: square_size - the side length in pixels that each square
                                  should be.
                                  
        Returns: - a pixbuf.
        """
        #prepares the image
        colours = 8
        chr_per_colour = 1
        first_line = "4 4 8 1"  #width, height, num of colours, chr per colour
        colour_key = ["  c #000",
                      "Z c #0FF",
                      "S c #0F0",
                      "T c #A00",
                      "I c #F00",
                      "O c #00F",
                      "L c #F0F",
                      "J c #FFF"]
                      
        #creates the picture
        picture = []
        o = 2 - self._next_piece_size // 2
        for y in range(4):
            line = ""
            for x in range(4):
                if (x-o, y-o) in self._next_piece_square.keys():
                    line += self._next_piece_square[x-o, y-o]
                else:
                    line += " "
            picture.append(line)
            
        #puts the various parts of the image together
        xpm_data = []
        xpm_data.append(first_line)
        xpm_data.extend(colour_key)
        xpm_data.extend(picture)
        
        #expands the image
        pixbuf = gtk.gdk.pixbuf_new_from_xpm_data(xpm_data)
        width = 4 * square_size
        height = 4 * square_size
        scaled_pixbuf = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, False, 8,
                                                                width, height)
        pixbuf.scale(scaled_pixbuf, 0, 0, width, height, 0, 0, square_size,
                                        square_size, gtk.gdk.INTERP_NEAREST)
        return scaled_pixbuf 
                
        
    def get_level(self):
        """Calculates what the current level is and returns it.
        """
        return (self._lines / 10 + 1)
        
    def get_score(self):
        """Returns: The current score.
        """
        return self._score
        
    def get_lines(self):
        """Returns: the number of lines that have been cleared.
        """
        return self._lines
    
    def timer(self):
        """This sub should be called every once in a while.
        
        Returns: The amount of time in milliseconds that the timer sub should
        be called next. None is returned if the timer sub shouldn't be run
        again.
        """
        moved_down = Tetris.s_drop(self, False)
        if not moved_down: #the piece reached the bottom
            #adds the new piece to the field
            self._field_square = self._concat_squares()
            #erases the piece
            self._piece_square = {}
            #checks if lines can be cleared
            self._clear_lines()
            #creates a new piece
            created = self._create_new_piece()
            if not created:
                return None
        return_val = 5000 / (self.get_level() * 2 + 7)
        return return_val

    def s_drop(self, get_points=True):
        """Checks to see if the piece will move down by one and moves it if
        possible.
        
        Parameters: get_points- A boolean value to indicate if the the player
                                should recieve points for the piece moving
                                down. This should be True (the default value)
                                except for internal usage.
        
        Returns: True is the piece was moved down, otherwise False if the
        piece could not move down.
        """
        #moves the pice down
        return_flag = True
        if self._collide(y_offset=1):
            return_flag = False
        else:
            self._piece_y += 1
        #adds on the score
        if get_points:
            self._score += self.DROP_VAL
        
        return return_flag
        
    def h_drop(self):
        """Moves the piece down as far as it can go only stopping when there
        is an occupied square below.
        """
        while True:
            went_down = self.s_drop(True)
            if not went_down: break
        self.timer()
        
    def rotate(self, direction=True):
        """Rotates the squares in _piece_square such that the piece is rotated.
        
        Parameter: direction - detrimines the direction that the piece turns.
                               True is anti-clockwise and False is clockwise.
                               Defaults to True (anti-clockwise).
        """
        #Checks for certain pieces which should be rotates the opposite way
        #every second rotation. Otherwise, their symitry causes them to
        #'jump' sideways and up & down.
        if self._piece_square[self._piece_square.keys()[0]] in ('I', 'Z', 'S'):
            if self._piece_times_rotated % 2 == 0:
                direction = not direction
        #rotates the piece
        new_square = {}
        for x, y in self._piece_square.keys():
            if direction: #anti-clockwise
                new_x = y
                new_y = self._piece_size - x - 1
            else: #clockwise
                new_x = self._piece_size - y - 1
                new_y = x
            new_square[new_x, new_y] = self._piece_square[x, y]
        if not self._collide(piece=new_square):
            self._piece_square = new_square
            self._piece_times_rotated += 1
        
    def sideways(self, direction):
        """Moves the piece to the left or to the right.
        
        Parameters: direction - The direction that the piece is moved. 'L' is
                                left and 'R' is right.
        """
        if direction == 'L':
            if not self._collide(x_offset=-1):
                self._piece_x -= 1
        elif direction == 'R':
            if not self._collide(x_offset=1):
                self._piece_x += 1
        
    def _create_next_piece(self):
        """Creates a new piece and stores it in self._next_piece_square.
        This is the next piece that will appear at the top of the playing
        field.
        """
    
        #creates the piece for next time
        piece_type = random.choice(self.PIECE_TUPLE)
        self._next_piece_square = {}
        if piece_type == 'Z':
            self._next_piece_square[0, 0] = 'Z'
            self._next_piece_square[1, 0] = 'Z'
            self._next_piece_square[1, 1] = 'Z'
            self._next_piece_square[2, 1] = 'Z'
            self._next_piece_size = 3
        if piece_type == 'S':
            self._next_piece_square[2, 0] = 'S'
            self._next_piece_square[1, 0] = 'S'
            self._next_piece_square[1, 1] = 'S'
            self._next_piece_square[0, 1] = 'S'
            self._next_piece_size = 3
        if piece_type == 'T':
            self._next_piece_square[1, 0] = 'T'
            self._next_piece_square[0, 1] = 'T'
            self._next_piece_square[1, 1] = 'T'
            self._next_piece_square[2, 1] = 'T'
            self._next_piece_size = 3
        if piece_type == 'I':
            self._next_piece_square[0, 1] = 'I'
            self._next_piece_square[1, 1] = 'I'
            self._next_piece_square[2, 1] = 'I'
            self._next_piece_square[3, 1] = 'I'
            self._next_piece_size = 4
        if piece_type == 'O':
            self._next_piece_square[0, 0] = 'O'
            self._next_piece_square[0, 1] = 'O'
            self._next_piece_square[1, 0] = 'O'
            self._next_piece_square[1, 1] = 'O'
            self._next_piece_size = 2
        if piece_type == 'L':
            self._next_piece_square[1, 0] = 'L'
            self._next_piece_square[1, 1] = 'L'
            self._next_piece_square[1, 2] = 'L'
            self._next_piece_square[2, 2] = 'L'
            self._next_piece_size = 3
        if piece_type == 'J':
            self._next_piece_square[1, 0] = 'J'
            self._next_piece_square[1, 1] = 'J'
            self._next_piece_square[1, 2] = 'J'
            self._next_piece_square[0, 2] = 'J'
            self._next_piece_size = 3
        
    def _create_new_piece(self):
        """Takes the next piece and stores the coordinate data in
        _piece_square.
        
        Returns: True if the piece is created succesfully ie it does not
        collide with any existing squares upon creation. Returns False
        otherwise.
        """

        #initiations the position and times rotated
        self._piece_times_rotated = 0
        self._piece_x = (self._width - self._next_piece_size) / 2
        self._piece_y = 0
        
        #checks for a collision
        if self._collide(piece=self._next_piece_square):
            return_val = False
        else:
            #assigns the next piece to the current piece
            self._piece_square = self._next_piece_square
            self._piece_size = self._next_piece_size
            return_val = True
            
        self._create_next_piece()
            
        return return_val
   
    def _clear_lines(self):
        """Checks if there are any lines that can be cleared and clears them.
        """
        lines_cleared = 0
        for y in range(self._height):
            #looks for a full line
            line_full = True
            for x in range(self._width):
                if (x, y) not in self._field_square.keys():
                    line_full = False
            #erases the line        
            if line_full:
                lines_cleared += 1
                for x in range(self._width):
                    del self._field_square[x, y]
            #moves the pices above the line down
            if line_full:
                for num in range(y, -1, -1):
                    for x in range(self._width):
                        if (x, num - 1) in self._field_square.keys():
                            self._field_square[x, num] = self._field_square[x, num - 1]
                            del self._field_square[x, num - 1]
        #adds to the score and lines
        self._score += self.LINE_VAL * lines_cleared * (lines_cleared + 1) / 2
        self._lines += lines_cleared
        
    def _concat_squares(self):
        """Returns: a concatinated dictionary of the positions of where squares
        from _field_square and _piece_square are located.
        """
        concat_dict = {}
        for x, y in self._field_square.keys():
            concat_dict[x, y] = self._field_square[x, y]
        for x, y in self._piece_square.keys():
            concat_dict[x + self._piece_x, y + self._piece_y] = \
                                                    self._piece_square[x, y]
        return concat_dict
        
    def _collide(self, piece=None, field=None, x_offset=0, y_offset=0):
        """Checks if the squares given by _piece_square and _field_square are
        refered to the same position.
        
        Parameters: piece    - The dictionary containing piece information.
                               The default value is self._piece_square
                    field    - The dictionary containing field information.
                               The default value is self._field_square
                    x_offset - The offset for the first part of the tuple in
                               _piece_square.
                    y_offset - The offset for the second part of the tuple in
                               _piece_square.
                               
        Returns: True if there was a collision or False otherwise.
        """
        #sets default values
        if piece == None:
            piece = self._piece_square
        if field == None:
            field = self._field_square
        #checks for a collision
        flag = False
        for x, y in piece.keys():
            x_to_check = x + self._piece_x + x_offset
            y_to_check = y + self._piece_y + y_offset
            if (x_to_check, y_to_check) in field.keys(): #checks for collision
                flag = True                              #with existing squares
            if x_to_check < 0 or x_to_check >= self._width:  #checks collision
                flag = True                                  #with field side
            if y_to_check >= self._height:  #checks collision
                flag = True                 #with bottom of field
        return flag[/PHP]

---

### Post by LaRoza on 2008-01-18
Very nice.

It handles much better than the tetris clone that comes with Ubuntu.

---

### Post by Wybiral on 2008-01-18
Looks good.

/me edits the random choice to increase chances of pole shape...

---

### Post by NovaAesa on 2008-01-18
Glad you guys like it!

---

### Post by Vadi on 2008-01-18
Thank you, looks like a great example to get started with Python and GTK.

---

### Post by Kadrus on 2008-01-19
Nice job NovaAesa :)

---

### Post by Quikee on 2008-01-19
The code is easy to read I am satisfied how you document and comment it. 

On the other hand you use classes - a object-oriented feature, but your code is not object oriented at all. If I think about how to code tetris (I must say I never tried to write one tetris game myself) I see at least the following objects/classes:

general Piece -  a class that shares everything all pieces have in common.

specific pieces - classes for each "shape" of a piece with its own specific behavior.

Good work!

---

### Post by NovaAesa on 2008-01-20
Now you say that, I realise I could have used classes a bit more effectively. I might rewrite some of the code to encorporate more OO features.

Thanks for the constructive criticism :)

---

