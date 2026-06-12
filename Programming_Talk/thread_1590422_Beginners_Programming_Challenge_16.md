---
title: "Beginners Programming Challenge 16"
date: 2010-10-07
forum: Programming Talk
---

### Post by pedro3005 on 2010-10-07
The challenge now is related to the Conway's Game of Life. Yes - you must create a program which emulates it.
Rules: [http://en.wikipedia.org/wiki/Conway%27s_Game_of_Life](http://en.wikipedia.org/wiki/Conway%27s_Game_of_Life)
You may consider dead anything outside the bounds of the grid.
Input: the program will be called with two arguments: a file containing the original state and (being it a square) the length of the side of the grid.
The file: it will be a string of 0's and 1's - 0 means a dead cell, 1 means a live cell. Example file:
```

0000000000000000000000000000000000000011000001100000000011000110000000100101010100100001110110110111000001010101010100000001110001110000000000000000000000000111000111000000010101010101000001110110110111000010010101010010000000110001100000000011000001100000000000000000000000000000000000000

```Being this in a file named 'pulsar', this should merrily display the pulsar pattern being called by:
```
./gol pulsar 17
```It should display: [http://upload.wikimedia.org/wikipedia/en/0/07/Game_of_life_pulsar.gif](http://upload.wikimedia.org/wikipedia/en/0/07/Game_of_life_pulsar.gif)
Displaying: get creative. If you have no GUI experience, a terminal displaying is completely acceptable.

---

### Post by bunburya on 2010-10-08
Can we presume that the length of the file will be (or should be) the exact right length? Because if so we needn't really take the length of the side, surely. Or might the input file be longer than we need?

---

### Post by alex_vr on 2010-10-08
Is it okay to use a non standard library? 
This is my first challenge so I don't know the rules.
Language is C++ and SFML for the graphics.

[PHP]
#include <iostream>
#include <vector>
#include <fstream>
#include <sstream>
#include <SFML/Graphics.hpp>

typedef std::vector< std::vector<char> > matrix_type;

struct Point
{
    Point(int x = 0, int y = 0) 
        : x(x),y(y){}
    int x;
    int y;
};

int ToInt(const std::string& str) 
{
    std::istringstream is(str);
    int x = 0;
    is >> x;
    return x;
}

void PrintMatrix(const matrix_type& matrix)
{
    for(int i = 0; i < matrix.size(); ++i)
    {
        for(int j = 0; j < matrix[i].size(); ++j)
            std::cout << matrix[i][j];    
        std::cout << "\n";
    }
    std::cout << "\n";
}

void LoadMatrix(matrix_type& matrix, std::ifstream& isfile)
{
    for(int i = 0; i < matrix.size(); ++i)
        for(int j = 0; j < matrix.size(); ++j)
            isfile >> matrix[i][j];
}

const int PossibleMovements = 8;

const Point Movements[PossibleMovements] = 
{
    Point(1, 0),  Point(-1, 0), 
    Point(0, 1),  Point(0, -1), 
    Point(1, 1),  Point(1, -1), 
    Point(-1, 1), Point(-1, -1)
};

enum State{Dead = '0', Alive = '1'};

void ChangeState(matrix_type& matrix, int row, int col, std::vector<Point>& changes)
{
    int count = 0;
    for(int i = 0; i < PossibleMovements; ++i)
    {
        int x = Movements[i].x + col;
        int y = Movements[i].y + row;
        if(x < 0 || y < 0 || x >= matrix.size() || y >= matrix.size() )
            continue;
        if(matrix[y][x] == Alive) ++count;
    }
    if(matrix[row][col] == Alive )
    {
        if(count < 2 || count > 3)
            changes.push_back(Point(col, row) );    
    }
    else if(count == 3)
        changes.push_back( Point(col, row) );
}

void Pulse(matrix_type& matrix)
{
    std::vector<Point> changes;
    for(int i = 0; i < matrix.size(); ++i)
        for(int j = 0; j < matrix.size(); ++j)
            ChangeState(matrix, i, j, changes);
    for(int i = 0; i < changes.size(); ++i)
    {    
        char& c = (matrix[changes[i].y][changes[i].x]);
        c = (c == '0') ? ('1') : ('0');
    }    
    
}

void CommandLine(matrix_type& matrix)
{
    PrintMatrix(matrix);
    
    while(std::cin.get())
    {        
        Pulse(matrix);
        PrintMatrix(matrix);
        std::cout << "Enter - Next pulse\n";
    }
}

void Graphics(matrix_type& matrix)
{
    sf::RenderWindow app(sf::VideoMode(800, 600), "Life");
    const int TileSize = 10;
    
    sf::Clock timer;    
    while(app.IsOpened())
    {
        sf::Event event;
        while(app.GetEvent(event))
            if(event.Type == sf::Event::Closed)
                app.Close();    
        
        app.Clear();
        if(timer.GetElapsedTime() > 0.5f)
        {
            Pulse(matrix);        
            timer.Reset();    
        }
        for(int i = 0; i < matrix.size(); ++i)
        {
            for(int j = 0; j < matrix.size(); ++j)
                if(matrix[i][j] == Alive)
                    app.Draw(sf::Shape::Rectangle(TileSize * j, TileSize * i, TileSize, TileSize, sf::Color::Red));
        }        
        app.Display();
    }
}

void Run(matrix_type& matrix)
{
    std::cout << "Graphics? [Y/N]: ";
    char answer;
    std::cin >> answer;
    
    if(std::tolower(answer) == 'y')
        Graphics(matrix);
    else
        CommandLine(matrix);    
}

int main(int argc, char** argv)
{    
    if(argc < 3)
    {
        std::cout << "Usage: " << argv[0] << " <filename> <size>\n";
        return 1;        
    }
    
    std::ifstream isfile(argv[1]);    
    if(!isfile)
    {
        std::cout << "Error: bad filename\n";
        return 1;
    }
    
    
    const int Size = ToInt(argv[2]);
    
    matrix_type matrix(Size, std::vector<char>(Size));
    LoadMatrix(matrix, isfile);
        
    Run(matrix);
}    



/*
CPP=g++
FLAGS=-Wall -Wextra -pedantic -ansi
LIBS=-lsfml2-graphics -lsfml2-window -lsfml2-system


Main:    main.o
    $(CPP) $(FLAGS) -o Main main.o $(LIBS)
    
    
Main.o: main.cpp
    $(CPP) -c main.cpp
*/
[/PHP]

---

### Post by pedro3005 on 2010-10-08
Yes the file will be the right length. I realize that you can do without the size, bonus points I guess.
To the non-standard library, can I download it from the ubuntu repo?

---

### Post by schauerlich on 2010-10-09
Here's a few more patterns for people to test with. I'll withhold my code until some more real entries are in. :)

[Beacon](http://en.wikipedia.org/wiki/File:Game_of_life_beacon.gif) (4x4)
```
1100110000110011
```

[Glider](http://en.wikipedia.org/wiki/File:Game_of_life_animated_glider.gif) (10x10)
```
0010000000101000000001100000000000000000000000000000000000000000000000000000000000000000000000000000
```

[Gosper's Glider Gun](http://upload.wikimedia.org/wikipedia/commons/e/e5/Gospers_glider_gun.gif) (38x25) (Very cool)
```
00000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000010100000000000000000000000001100000011000000000000110000000000000100010000110000000000001100110000000010000010001100000000000000001100000000100010110000101000000000000000000000001000001000000010000000000000000000000001000100000000000000000000000000000000001100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
```

38x38 if your program requires the board to be square:
```
0000000000000000000000000000000000000000000000000000000000000001000000000000000000000000000000000001010000000000000000000000000110000001100000000000011000000000000010001000011000000000000110011000000001000001000110000000000000000110000000010001011000010100000000000000000000000100000100000001000000000000000000000000100010000000000000000000000000000000000110000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
```

---

### Post by Bodsda on 2010-10-09
Is the program supposed to emulate the game of life as well, should the image change or is it just the initial snapshot of the image?

---

### Post by pedro3005 on 2010-10-09
Yes, it should emulate it. The image should change according to the rules of the game. Tip: make a waiting time between the changes so I can actually observe them.

---

### Post by schauerlich on 2010-10-09
EDIT: nevermind

---

### Post by mo.reina on 2010-10-09
code has been re-factored, combined the algorithm for checking changes in rows above and below.

Python 3.1:
```
import os

import sys

import time

def create_matrix(data, row_length):
    master_list = []
    temp_list = []
    count = 0
    for number in data:
        temp_list.append(number)
        count += 1
        if count % row_length == 0:
            master_list.append(temp_list)
            count = 0
            temp_list = []
    return master_list

def adjacent_row(matrix, row, el):
    # testing for row existence of a row below the current cell
    try:
        temp = matrix[row]
        if row  >= 0:
            if (el - 1)  >= 0:
                neighbor_a = matrix[row][el - 1]
            else:
                neighbor_a = 0
            neighbor_b = matrix[row][el]
            try:
                neighbor_c = matrix[row][el + 1]
            except IndexError:
                neighbor_c = 0
        else:
            neighbor_a, neighbor_b, neighbor_c = 0, 0, 0
    except IndexError:
        neighbor_a, neighbor_b, neighbor_c = 0, 0, 0
    return neighbor_a, neighbor_b, neighbor_c

def same_row(matrix, row, el):
    if (el - 1) >= 0:
        neighbor1 = matrix[row][el - 1]
    else:
        neighbor1 = 0
    try:
        neighbor2 = matrix[row][el + 1]
    except IndexError:
        neighbor2 = 0
    return neighbor1, neighbor2

def map_cells(matrix):
    row = 0
    el = 0
    new_row = []
    while row != len(matrix):
        cell = matrix[row][el]
        #numbers surroundin the cell are called neighbors
        neighbor1, neighbor2 = same_row(matrix, row, el)
        #calculates change for row below current one
        neighbor3, neighbor4, neighbor5 = adjacent_row(matrix, (row + 1), el)
        #calculates change for row above current one
        neighbor6, neighbor7, neighbor8 = adjacent_row(matrix, (row - 1), el)
        total = neighbor1 + neighbor2 + neighbor3 + neighbor4 + neighbor5 + neighbor6 + neighbor7 + neighbor8
        #calculates if cell lives, dies, or is reborn
        if total < 2 or total > 3:
            cell = 0
        if cell == 0:
            if total == 3:
                cell = 1
        el += 1
        if el > len(matrix[row]) - 1:
            row += 1
            el = 0
        new_row.append(cell)
    return new_row
     
def main():
    with open(sys.argv[1]) as f:
        f = f.read()
    #convert numbers in file to list
    row = [int(i) for i in f.replace('\n', '')]
    matrix = create_matrix(row, int(sys.argv[2]))
    while True:
        os.system('clear')
        for line in matrix:
            for el in line:
                #print out blocks instead of 1 and 0 for easier visual representation
                if el == 1:
                    print("\u25FC", end='')
                else:
                    print("\u25FB", end='')
            print()
        time.sleep(0.5)
        new_row = map_cells(matrix)
        matrix = create_matrix(new_row, int(sys.argv[2]))
    
if __name__ == "__main__":
    main()
```

---

### Post by schauerlich on 2010-10-09
> **mo.reina said:**
> by the way, can anyone point me to a site that has the initial patterns?

I wrote a few [here](http://ubuntuforums.org/showpost.php?p=9942852&postcount=5) you can use to test.

---

### Post by dv3500ea on 2010-10-09
This is a very interesting and fun challenge :) .

@mo.reina: I like your idea of using the unicode boxes; they make it easier to read than the +s and -s that I was using.

A note of warning for those taking part: don't modify your grid in place. You need to make a full clone of your data structure, applying the rules to the original but writing to the clone. Otherwise the patterns get messed up! (I made this mistake at first and it took me ages to work out what the problem was :oops:).

I look forward to seeing everyones' solutions and will post my (ruby) version after the challenge has been judged.

---

### Post by Some Penguin on 2010-10-09
Some fun extensions to try:

* Multiple species:  anything but 0 is a species, amend the dead cell -> live cell rule to pick a majority if present and randomly otherwise.
* Steady-state detection.
* Cycle detection, a superproblem of the previous.


```

0010000010000001110000000000000022200002000000020

```

has a sample 6x6 grid w/ 2 gliders; according to my sim (a very uninteresting and straightforwards Perl implementation -- one module which does the computation, and one driver script which handles reading the file and outputing results to STDOUT; never bothered to learn any graphic modules for Perl), glider #2 is gone 4 iterations after the start state, and 6 iterations after the start state a steady state is reached w/ 6 1's.

---

### Post by mo.reina on 2010-10-10
> **schauerlich said:**
> I wrote a few [here](http://ubuntuforums.org/showpost.php?p=9942852&postcount=5) you can use to test.

hey schauerlich, i've used the sequences you posted.  i was wondering if you found them on an external site or did you just reverse engineer (count the cells manually) the patterns that you found on the 'net?

---

### Post by schauerlich on 2010-10-10
> **mo.reina said:**
> hey schauerlich, i've used the sequences you posted.  i was wondering if you found them on an external site or did you just reverse engineer (count the cells manually) the patterns that you found on the 'net?

I just used pictures from wikipedia and "drew" them myself in a text editor, and removed all the newlines.

[img]http://grab.by/grabs/d1671837c5635b16f2364990861f681d.png[/img]
```

1100
1000
0001
0011
=>
1100100000010011
```

---

### Post by Some Penguin on 2010-10-10
Well, there are quite a few patterns in Wikipedia...

For amusement:
```

.........................................                                                                                                                                    
..........................O..............                                                                                                                                    
........................O.O..............                                                                                                                                    
..............OO......OO............OO...                                                                                                                                    
.............O...O....OO............OO...                                                                                                                                    
..OO........O.....O...OO.................                                                                                                                                    
..OO........O...O.OO....O.O..............                                                                                                                                    
............O.....O.......O..............                                                                                                                                    
.............O...O.......................                                                                                                                                    
...............OO........................                                                                                                                                    
.........................................

```

(sourced from [http://en.wikipedia.org/wiki/File:Game_of_life_glider_gun.svg]("http://en.wikipedia.org/wiki/File:Game_of_life_glider_gun.svg"))

That's the Gosper glider gun, although I've taken the liberty of using periods instead of zeros and not cramming it into a single row so that it's actually easier to examine and check for errors.  If you separate your computational and I/O layers, it's not terribly inconvenient to have I/O methods that e.g. accept an alternate character for 'dead' space or cheerfully accept one-row-per-line.


```


: # Find perl...
eval 'exec perl5 -w -S $0 "$@"'
if 0;


my $line = undef;
my $colcount = undef;
my @lines = ();

while (defined($line = <STDIN>)) {
        $line =~ s/\n$//go;
        ((length $line) > 0) || next;
        $line =~ tr/.O/01/;

        if (!defined($colcount)) {
                $colcount = length $line;
        } else {
                die unless ((length $line) == $colcount);
        }

        push @lines, $line;
}
print "$colcount\n";
print join("", @lines);
print "\n";

exit 0;

```

is Perl that accepts such a format (one row per line, . for empty, O for live) and outputs the number of columns followed by the 1/0 string.  It won't enforce squareness, however.

---

### Post by worksofcraft on 2010-10-10
Hey... this looks like fun :)
What they mean by "beginner" can anyone take part?
I mean I figure that not programming for 15 years must have set me back to beginner status right?

p.s when is it due by ?

---

### Post by nvteighen on 2010-10-10
> **worksofcraft said:**
> Hey... this looks like fun :)
What they mean by "beginner" can anyone take part?
I mean I figure that not programming for 15 years must have set me back to beginner status right?

p.s when is it due by ?

These challenges run forever :) And basically anybody that considers himself to be a beginner in some respect can participate.

I'm still struggling against this and I'm not sure if I'll ever be able to do it... having some little spare time in my hands :(

---

### Post by ziekfiguur on 2010-10-10
Well, this may not be the cleanest or most efficient code i ever wrote. But its working and it's got a gui :P

```

#!/usr/bin/env python

import sys
import pygtk
pygtk.require('2.0')
import gtk
import gobject

class GOL:
    def __init__(self, infile, gridsize):
        self.gridsize = gridsize
        self.grid = [[0 for i in range(self.gridsize)] for i in range(self.gridsize)]
        start = open(infile, 'r')
        for y in range(self.gridsize):
            for x in range(self.gridsize):
                s = start.read(1)
                if not s:
                    break
                self.grid[y][x] = int(s)

        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title('GOL')
        self.window.connect('destroy', lambda w : gtk.main_quit())

        self.da = gtk.DrawingArea()
        self.da.set_size_request(4 * self.gridsize, 4 * self.gridsize)

        self.window.add(self.da)

        self.window.show_all()
        self.da.connect("expose-event", self.draw_state)

        self.pixmap = gtk.gdk.Pixmap(None, 4 * self.gridsize, 4 * self.gridsize, 24)

        self.style = self.da.get_style()
        self.gc = self.style.fg_gc[gtk.STATE_NORMAL]
        self.black = self.gc.get_colormap().alloc_color(0, 0, 0)
        self.white = self.gc.get_colormap().alloc_color(65535, 65535, 65535)
        self.gc.set_rgb_bg_color(self.black)
        self.gc.set_rgb_fg_color(self.white)

        self.draw_state()

        self.timeout_id = gobject.timeout_add(200, self.next_state)


    def draw_state(self, widget = None, data = None):
        self.gc.set_rgb_fg_color(self.black)
        self.pixmap.draw_rectangle(self.gc, True, 0, 0, 4 * self.gridsize, 4 * self.gridsize)
        self.gc.set_rgb_fg_color(self.white)
        for y in range(self.gridsize):
            for x in range(self.gridsize):
                if self.grid[y][x]:
                    self.pixmap.draw_rectangle(self.gc, True, x * 4, y * 4, 4, 4)
        self.da.window.draw_drawable(self.gc, self.pixmap, 0, 0, 0, 0, 4 * self.gridsize, 4 * self.gridsize)


    def next_state(self):
        newgrid = [[0 for i in range(self.gridsize)] for i in range(self.gridsize)]
        max = self.gridsize - 1
        for y in range(self.gridsize):
            for x in range(self.gridsize):
                around = 0
                if x > 0    and self.grid[y][x - 1]: around += 1
                if x < max  and self.grid[y][x + 1]: around += 1
                if y > 0    and self.grid[y - 1][x]: around += 1
                if y < max  and self.grid[y + 1][x]: around += 1
                if x > 0    and y > 0   and self.grid[y - 1][x - 1]: around += 1
                if x < max  and y > 0   and self.grid[y - 1][x + 1]: around += 1
                if x > 0    and y < max and self.grid[y + 1][x - 1]: around += 1
                if x < max  and y < max and self.grid[y + 1][x + 1]: around += 1

                if around == 3:
                    newgrid[y][x] = 1
                elif around == 2 and self.grid[y][x]:
                    newgrid[y][x] = 1
        self.grid = newgrid
        self.draw_state
        self.da.queue_draw()
        return True

def main(argv):
    gol = GOL(argv[1], int(argv[2]))
    gtk.main()

if __name__ == '__main__':
    main(sys.argv)

```

---

### Post by worksofcraft on 2010-10-10
> **nvteighen said:**
> These challenges run forever :) And basically anybody that considers himself to be a beginner in some respect can participate.

Kewl :)

Well I always fancied having an excuse to write something using ncurses, so here is one I slapped together just now and I include initial setting "seed" file in the archive too. Anyone else is welcome to hack it for their own ends.

p.s. OK so I got a moment to have another look and I see the rule is different for dead cells than living cells so I think I fixed now and also I made it so it should work with non rectangular seed files by specifying the number of rows and calculating number of columns... but that glider gun I copied from above still doesn't work :(

---

### Post by worksofcraft on 2010-10-10
OK that glider gun has a buglet and I adapted my code to allow new lines (or anything other than a 1) for non living cells and so now it does work. I also added some extra lines so you can see the gliders as they go:
```

........................................
..........................1.............
........................1.1.............
..............11......11............11..
.............1...1....11............11..
..11........1.....1...11................
..11........1...1.11....1.1.............
............1.....1.......1.............
.............1...1......................
..............11........................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................

```
Do specify the height as 25 lines tho as it's not a square.

btw the sample in post #5 given by schauerlich does work, it's the one in post 15 that has an error on line 10.

---

### Post by alex_vr on 2010-10-10
> **pedro3005 said:**
> Yes the file will be the right length. I realize that you can do without the size, bonus points I guess.
To the non-standard library, can I download it from the ubuntu repo?

The version of the library I'm using is not yet in the repositories.

---

### Post by worksofcraft on 2010-10-11
I found [comprehensive library of patterns ]("http://www.radicaleye.com/lifepage/patterns/contents.html") and there is a Java applet that renders them. It looks like they don't surround the field with dead cells but let things wrap round. It would be nice to know the file format so we can try them in our own gol apps too.

---

### Post by appi2012 on 2010-10-12
Here is my sumbission. It creates a gtk window with the grid and controls to start/pause the animation, and a slider to control the speed. Here is the code of gol.py:

```
import time
import sys
import pygtk
pygtk.require('2.0')
import gtk
import gobject

class GOL:
	def __init__(self, w, h, s):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title('GOL')
		self.window.connect('destroy', lambda w : gtk.main_quit())
		self.width = w
		self.height = h
		self.string = s
		self.grid = [[0 for i in range(self.height)] for j in range(self.width)]
		self.loadgrid()
	
		self.running = False
		self.speed = 200

		self.gridarea = gtk.DrawingArea()
		self.gridarea.set_size_request(8 * self.width +1, 8 * self.height+1)
		
		self.closer = gtk.Button("Close")
		self.closer.connect("clicked", lambda w : gtk.main_quit())

		self.playcontrol = gtk.Button("Play")
		self.playcontrol.connect("clicked", self.playpause)

		self.speedlabel = gtk.Label("Speed:")
		self.speedslider = gtk.HScale()
		self.speedslider.set_range(1, 20)
		self.speedslider.set_value(5)
		self.speedslider.connect("value-changed", self.changespeed)

		self.buttonbox = gtk.HBox(False, 10)
		self.buttonbox.pack_start(self.playcontrol, False)
		self.buttonbox.pack_start(self.speedlabel, False)
		self.buttonbox.pack_start(self.speedslider, True)
		self.buttonbox.pack_end(self.closer, False)
		self.box = gtk.VBox(False, 10)
		self.box.pack_start(self.gridarea, True)
		self.box.pack_end(self.buttonbox, False)
		self.box.set_border_width(10)
		self.window.add(self.box)
	
		self.window.show_all()
		self.gridarea.connect("expose-event", self.drawgrid)
	
		self.pixmap = gtk.gdk.Pixmap(None, 8 * self.width +1, 8 * self.height +1, 24)
	
		self.style = self.gridarea.get_style()
		self.gc = self.style.bg_gc[gtk.STATE_NORMAL]
		self.fc = self.style.bg_gc[gtk.STATE_SELECTED]
		self.rc = self.style.fg_gc[gtk.STATE_NORMAL]
		self.ic = self.style.bg_gc[gtk.STATE_INSENSITIVE]
		self.drawgrid()
	


	def drawgrid(self, widget = None, data = None):
		self.pixmap.draw_rectangle(self.gc, True, 0, 0, 8 * self.width, 8 * self.height)
		for x in range(self.width):
			for y in range(self.height):
		    		if self.grid[x][y]==1:
		        		self.pixmap.draw_rectangle(self.fc, True, x * 8, y * 8, 7, 7)
		        	else:
		        		self.pixmap.draw_rectangle(self.ic, True, x * 8, y * 8, 7, 7)
		self.pixmap.draw_rectangle(self.rc, False, 0, 0, self.width*8-1, self.height*8-1)
	        self.gridarea.window.draw_drawable(self.fc, self.pixmap, 0, 0, 0, 0, 8 * self.width, 8 * self.height)

	def loadgrid(self):
		i=0
		for y in range(self.height):
			for x in range(self.width):
				self.grid[x][y] = int(self.string[i])
				i+=1

	def neighbors(self, col, row):
		cells = 0
		for x in range(3):
			for y in range(3):
				try:
					if self.grid[col-x+1][row-y+1] == 1:
						cells+=1
						if max(0, col-x+1) == 0 or max(0,row-y+1) == 0:
							cells-=1
				except IndexError:
					a = 1 #Do nothing
		if self.grid[col][row] == 1:
			cells-=1
		return cells
	
	def changegrid(self):
		grid2 = [[0 for i in range(self.height)] for j in range(self.width)]
		for x in range(self.width):
			for y in range(self.height):
				if self.neighbors(x,y) == 3:
					grid2[x][y] = 1
				elif self.grid[x][y] == 1 and self.neighbors(x,y) == 2:
					grid2[x][y] = 1

					
		self.grid = grid2
		self.drawgrid()
		self.gridarea.queue_draw()
		if self.running:
        		return True
		else:
			return False

	def playpause(self, widget = None, data = None):
		if self.running:
			self.running = False;
			gobject.idle_add(self.speedslider.set_sensitive, True)
			self.playcontrol.set_label("Play")
		else:
			self.running = True;
			self.timeout_id = gobject.timeout_add(self.speed, self.changegrid)
			gobject.idle_add(self.speedslider.set_sensitive, False)
			self.playcontrol.set_label("Pause")

	def changespeed(self, widget=None, data=None):
		self.speed = int(1000/self.speedslider.get_value())


filename = open(sys.argv[1])
string = filename.read()
width = int(sys.argv[2])
height = len(string)/width

if __name__ == '__main__':
	gol = GOL(width, height, string)
	gtk.main()

		
```

You run it by typing:
```
python /path/to/gol.py /path/to/inputfile [number of cells in one row]
```

For example:
```
python gol.py glidergun 38
```

Also, if anyone wants another inputfile to test, here's one I put together:
**An Oscillator (13 by 13)**```
0000000000000000000000000000000000000000000000000000000011011000000011000110000000110110000001010001010000010000010000000000000000000000000000000000000000000000000000000
```

---

### Post by bioShark on 2010-10-12
Here is my solution. It's Java. Unfortunatelly I have't had the time now to create a GUI, so for now it's text display only. The example in the code is Beacon (period 2), but it should work with any layout. For now you also have to specify the number of generations to run (default now 10).

```
package stuff;

public class Layout {

    private int[][] layout;

    public Layout(int[][] lay) {
        setLayout(lay);
    }
    
    public int getCell(Layout lay, int height, int length) {
        return lay.getLayout()[height][length];
    }
    
    public int getLiveNeighbours(Layout lay, int height, int length) {
        int liveNeighbours = 0;

        liveNeighbours += (getCellState(lay, height - 1, length - 1) == 1) ? 1 : 0;
        liveNeighbours += (getCellState(lay, height - 1, length) == 1) ? 1 : 0;
        liveNeighbours += (getCellState(lay, height - 1, length + 1) == 1) ? 1 : 0;
        liveNeighbours += (getCellState(lay, height, length - 1) == 1) ? 1 : 0;
        liveNeighbours += (getCellState(lay, height, length + 1) == 1) ? 1 : 0;
        liveNeighbours += (getCellState(lay, height + 1, length - 1) == 1) ? 1 : 0;
        liveNeighbours += (getCellState(lay, height + 1, length) == 1) ? 1 : 0;
        liveNeighbours += (getCellState(lay, height + 1, length + 1) == 1) ? 1 : 0;

        return liveNeighbours;
    }

    public int returnChangedState(Layout lay, int height, int length) {
        int value = lay.getLayout()[height][length];
        return (value == 0) ? 1 : 0;
    }

    public int getCellState(Layout lay, int height, int length) {
        if (height < 0 || height >= lay.getNumberOfLines() || length < 0
                || length >= lay.getNumberOfColumns()) {
            return -1;
        }
        return lay.getLayout()[height][length];
    }
    
    public boolean isCellAlive(Layout lay, int height, int length) {
        return (lay.getLayout()[height][length] == 1) ? true : false;
    }

    public boolean isCellDead(Layout lay, int height, int length) {
        return (lay.getLayout()[height][length] == 0) ? true : false;
    }

    public int getNumberOfLines() {
        return this.getLayout().length;
    }

    public int getNumberOfColumns() {
        return this.getLayout()[0].length;
    }

    public int[][] getLayout() {
        return layout;
    }

    public void setLayout(int[][] layout) {
        this.layout = layout;
    }

}

```

Layout class handles the layout (Obviously) 

Main class:
```
package main;

import java.io.IOException;

import stuff.Layout;

public class Game {

    public Game() {
    }
    
    public Layout applyRules(Layout lay) {
        int[][] newMatrix = new int[lay.getNumberOfLines()][lay
                .getNumberOfColumns()];
        int value = 0;
        boolean stored = false;
        for (int i = 0; i < lay.getNumberOfLines(); i++) {
            for (int j = 0; j < lay.getNumberOfColumns(); j++) {
                if (lay.isCellAlive(lay, i, j)) {
                    // rule 1
                    if (lay.getLiveNeighbours(lay, i, j) < 2) {
                        value = lay.returnChangedState(lay, i, j);
                        stored = true;
                    }
                    // rule 2 
                    if (lay.getLiveNeighbours(lay, i, j) > 3) {
                        value = lay.returnChangedState(lay, i, j);
                        stored = true;
                    }
                }
                // rule 4
                if (lay.isCellDead(lay, i, j) && lay.getLiveNeighbours(lay, i, j) == 3) {
                    value = lay.returnChangedState(lay, i, j);
                    stored = true;
                }                
                newMatrix[i][j] = (stored == true) ? value : lay.getCell(lay, i, j);
                value = 0;
                stored = false;
            }
        }
        Layout newLayout = new Layout(newMatrix);
        return newLayout;
    }

    public void printLayout(Layout lay) {
        for (int i = 0; i < lay.getNumberOfLines(); i++) {
            System.out.print("[");
            for (int j = 0; j < lay.getNumberOfColumns(); j++) {
                System.out.print(" " + lay.getCell(lay, i, j));
            }
            System.out.println(" ]");
        }
        System.out.println();
        System.out.println("-------------");
    }

    public static void main(String args[]) throws IOException {
        Game game = new Game();
        int[][] matrix = { 
                { 0, 0, 0, 0, 0, 0}, 
                { 0, 1, 1, 0, 0, 0},
                { 0, 1, 0, 0, 0, 0}, 
                { 0, 0, 0, 0, 1, 0}, 
                { 0, 0, 0, 1, 1, 0}, 
                { 0, 0, 0, 0, 0, 0}, 
                };
        Layout demo = new Layout(matrix);
        game.printLayout(demo);
        for (int i = 0; i < 10; i++) {
            Layout child = game.applyRules(demo);
            game.printLayout(child);
            demo = child;
        }
    }
}

```

---

### Post by Xender1 on 2010-10-12
Here is my solution. Wrote the code in C for some reason (started out doing it this way and just kept with it so it is all good), and for my graphics I use SDL. The only non standard libraries are SDL and I guess <unistd.h> for sleep. Here is main.c:

```


#include <stdio.h>
#include <stdlib.h>
#include <SDL/SDL.h>
#include <unistd.h>

enum {
    ALIVE = 1,
    DEAD = 0
};

void LoadFromFile(int **real_array, int array_size, FILE* file);
void GameOfLife(int **real_array,int **temp_array,int array_size,
    SDL_Surface* Back_Surf, SDL_Surface* tile_alive, SDL_Surface* tile_dead);
void PrintBoard(int **real_array,int array_size,
    SDL_Surface* Back_Surf, SDL_Surface* tile_alive, SDL_Surface* tile_dead);
int GetSurrounding(int **real_array, int array_size,int i,int j);
void OnEvent(SDL_Event *Event, int* running);

int main(int argc, char** argv) {
    if (argc != 3) { //fails if wrong # of args
        return -1;
    }
    //read in the args
    char* file_name = argv[1];
    int array_size = atoi(argv[2]);

    int **real_array; int **temp_array;
    real_array = malloc(sizeof(int *)*array_size); //create array'
    temp_array = malloc(sizeof(int *)*array_size);
    int i; int j;
    for (i=0;i<array_size;i++) {
        real_array[i] = malloc(sizeof(int)*array_size);
        temp_array[i] = malloc(sizeof(int)*array_size);
    }

    FILE* file = NULL;
    if ((file = fopen(file_name,"r"))== NULL) { //exits if cant open file
        return -1;
    }
    //read in initial conditions from file
    LoadFromFile(real_array,array_size,file);
    //set temp array to all deads
    for (i=0;i<array_size;i++) {
        for (j=0;j<array_size;j++) {
            temp_array[i][j] = DEAD;
        }
    }
    fclose(file);
    //set up our display device
    if (SDL_INIT_EVERYTHING<0) {
        return -1;
    }
    SDL_Surface* Back_Surf = NULL;
    //this video is *16 because my images are all 16x16 for each tile
    if ((Back_Surf = SDL_SetVideoMode(array_size*16,array_size*16,32,
            SDL_HWSURFACE | SDL_DOUBLEBUF))==NULL) {
        return -1; //failed at setting up display
    }
    //initial display settings too
    SDL_Surface* tile_alive = NULL;
    SDL_Surface* tile_dead = NULL;
    SDL_Surface* temp_tile_alive = NULL;
    SDL_Surface* temp_tile_dead = NULL;
    SDL_Event Event;

    if ((temp_tile_alive = SDL_LoadBMP("alive.bmp"))==NULL) {
        return -1;
    }
    if ((temp_tile_dead = SDL_LoadBMP("dead.bmp"))==NULL) {
        return -1;
    }
    tile_alive = SDL_DisplayFormat(temp_tile_alive);
    tile_dead = SDL_DisplayFormat(temp_tile_dead);
        SDL_FreeSurface(temp_tile_alive);
        SDL_FreeSurface(temp_tile_dead);

    //inital arrays created, lets draw initial board then play
    PrintBoard(real_array,array_size,Back_Surf,tile_alive,tile_dead);
    sleep(1);
    //THis is the game loop
    //SDL PollEVent is there so we can close the window
    int running = 1;
    while (running == 1) {
        GameOfLife(real_array,temp_array,array_size,
                         Back_Surf,tile_alive,tile_dead);
        sleep(1);
        while (SDL_PollEvent(&Event)) {
            if (Event.type == SDL_QUIT) {
                running = 0;
            }
        }
    }
    //cleanup
    SDL_FreeSurface(tile_alive);
    SDL_FreeSurface(tile_dead);
    SDL_FreeSurface(Back_Surf);

    SDL_Quit();
    return (1);
}

void LoadFromFile(int** real_array, int array_size,FILE* file) {
    char c; int i=0; int j=0;
    c = getc(file);
    while (c!=EOF) {
        int temp = atoi(&c); //convert to int
        real_array[i][j] = temp; //put in array
        j++;
        if (j==array_size) {
            j=0;i++; //reset j for next row if needed
        }
        c = getc(file);
    }
}

void PrintBoard(int** real_array, int array_size,
    SDL_Surface* Back_Surf, SDL_Surface* tile_alive, SDL_Surface* tile_dead) {
    int i; int j;
    SDL_Rect DestLoc;
    for(i=0;i<array_size;i++) {
        for (j=0;j<array_size;j++) {
                DestLoc.x = j * 16;
                DestLoc.y = i * 16;

                if (real_array[i][j] == ALIVE) {
                    SDL_BlitSurface(tile_alive,NULL,Back_Surf,&DestLoc);
                }
                if (real_array[i][j] == DEAD) {
                    SDL_BlitSurface(tile_dead,NULL,Back_Surf,&DestLoc);
                }
            }
        }
    SDL_Flip(Back_Surf);
}

void GameOfLife(int** real_array, int** temp_array, int array_size,
    SDL_Surface* Back_Surf, SDL_Surface* tile_alive, SDL_Surface* tile_dead) {
    //check for rules, create new real array and continue
    int i;int j;
    for(i=0;i<array_size;i++) {
        for (j=0;j<array_size;j++) {
            int neighbors = GetSurrounding(real_array,array_size,i,j);
            if (real_array[i][j] == ALIVE) { //rules for life and death
                if (neighbors < 2) {temp_array[i][j] = DEAD;}
                if (neighbors > 3) {temp_array[i][j] = DEAD;}
                if (neighbors == 2 || neighbors == 3) {temp_array[i][j]=ALIVE;}
            }
            else if ((real_array[i][j] == DEAD) && (neighbors == 3)) {
                temp_array[i][j] = ALIVE;
            }
            }
    }
    //now fill in real_array, reset dead array, and call again after a sec
    for (i=0;i<array_size;i++) {
        for (j=0;j<array_size;j++) {
            real_array[i][j] = temp_array[i][j];
            temp_array[i][j] = DEAD;
        }
    }

    PrintBoard(real_array,array_size,Back_Surf,tile_alive,tile_dead);
}

int GetSurrounding(int** real_array, int array_size, int i, int j) {
    //dont know how I could do this cleaner :/
    int around = 0;
    if ((i+1) != array_size) {
        if (real_array[i+1][j] == ALIVE) {
            around++;
        }
    }
    if ((i-1) != -1) {
        if (real_array[i-1][j] == ALIVE) {
            around++;
        }
    }
    if ((j+1) != array_size) {
        if (real_array[i][j+1] == ALIVE) {
            around++;
        }
    }
    if ((j-1) != -1) {
        if (real_array[i][j-1] == ALIVE) {
            around++;
        }
    }
    if (((i+1) != array_size) && ((j+1) != array_size)) {
        if (real_array[i+1][j+1] == ALIVE) {
            around++;
        }
    }
    if (((i+1) != array_size) && ((j-1) != -1)) {
        if (real_array[i+1][j-1] == ALIVE) {
            around++;
        }
    }
    if (((i-1) != -1) && ((j-1) != -1)) {
        if (real_array[i-1][j-1] == ALIVE) {
            around++;
        }
    }
    if (((i-1) != -1) && ((j+1) != array_size)) {
        if (real_array[i-1][j+1] == ALIVE) {
            around++;
        }
    }
    return around;
}


```

Now make sure for compiling that everything is in the same folder. 

You will need to use the .bmp images attached (just the squares from wiki and are 16px16p). Make sure to save one alive.bmp and the other dead.bmp (white is alive black is dead but pattern would be seen regardless).

This only works for square input files so for one with side 17 and the input in testfile.txt: 
```

0000000000000000000000000000000000000011000001100000000011000110000000100101010100100001110110110111000001010101010100000001110001110000000000000000000000000111000111000000010101010101000001110110110111000010010101010010000000110001100000000011000001100000000000000000000000000000000000000

```

compile with:
```

gcc -lSDL -o GameOfLife main.c
./GameOfLife testfile.txt 17

```

---

### Post by ja660k on 2010-10-13
Heh, im making one of these for a university assignment, in c++
the only difference is we need to be able to switch between 3 data structures at runtime.. an array, a hashtable and STL map. (to see which is more efficient)

and it reads in a file of co-ordinates from a file.

also, has anyone seen the GOL touring machine?
[http://rendell-attic.org/gol/tm.htm](http://rendell-attic.org/gol/tm.htm)

---

### Post by pedro3005 on 2010-11-11
I apologise for the long time it took to judge the entries. The results are now in, and the winner is:
[COLOR=Sienna]**appi2012**[/COLOR]
[COLOR=Black]Although I had to fix your code a little itsy bit (one line indented wrong, nothing major)[/COLOR], I loved the display you created, along with the grid. Very great work. To all other contestants, yes, you guys did great. One special shout out to ziekfiguur, yours looked really nice too! Let's get the ball rolling, everyone.

---

### Post by schauerlich on 2010-11-11
I was thinking about bumping this with my code. Seems like as good of a time as any to post it, seeing as it's not an entry. :)

Be warned, I'm by no means a Haskell programmer... but it works!

```
import System.IO
import System.Environment
import Control.Concurrent

data Cell = Dead | Alive deriving (Eq, Show)
type Row = [Cell]
type Board = [Row]



-- Cell functions

showCell :: Cell -> Char
showCell Alive = '@'
showCell Dead  = ' '

charToCell :: Char -> Cell
charToCell '1' = Alive
charToCell '0' = Dead

-- The main game logic. Takes a cell and its number of neighbors, and says
-- whether it lives or dies. Natural selection at its finest.
darwin :: Cell -> Int -> Cell
darwin cell n
  | n < 2  = Dead
  | n > 3  = Dead
  | n == 2 = if cell == Alive then Alive else Dead
  | n == 3 = Alive
             


-- Board Functions

showBoard :: Board -> String
showBoard board = unlines $ map (map (showCell)) board 

-- makeBoardFromStrings ["01", "00"] => [[Dead, Alive], [Dead, Dead]]
makeBoardFromStrings :: [String] -> Board
makeBoardFromStrings board@(r:rs) = map (map (charToCell)) board

-- Add an extra row/column of Dead on each side to simplify neighbor counting
padBoard :: Board -> Board
padBoard board = topRow:(newCore ++ [bottomRow])
  where 
    topRow = take ((length (head board)) + 2) $ repeat Dead
    bottomRow = topRow
    newCore = map (\x -> Dead:(x ++ [Dead])) board

-- Takes a board and its corresponding neighbor counts,
-- and generates the next generation's board
boardFromCounts :: Board -> [[Int]] -> Board
boardFromCounts board counts = splitEvery (length (head board)) newFlatBoard 
  where newFlatBoard = map (\(x,y) -> darwin x y) $ zip (flatten board) (flatten counts)

-- Takes a board and returns the next generation's board.
nextGeneration :: Board -> Board                  
nextGeneration board = boardFromCounts board $ neighborCounts $ padBoard board
                              
-- infinite (lazy) list of successive generations
generations :: Board -> [Board]
generations board = board:(generations (nextGeneration board))



-- neighbor calculations

-- Calculate the neighbors for the entire board, and return a grid
-- of neighbor counts
neighborCounts :: Board -> [[Int]]
neighborCounts board 
  | (length board) < 3 = []  
neighborCounts board@(prev:curr:next:rest) 
  | otherwise = (neighborCountOfRow prev curr next) : neighborCounts (tail board)

-- helper; does one row at a time, using the previous and next rows
-- in the calculations
neighborCountOfRow :: Row -> Row -> Row -> [Int]
neighborCountOfRow prev curr next 
  | (length prev) < 3 = []
  | otherwise  = (foldl (\count x -> if x == Alive then count+1 else count) 0 neighbors)
                 : (neighborCountOfRow (tail prev) (tail curr) (tail next))
  where
    top = take 3 prev
    middle = [curr !! 0, curr !! 2]
    bottom = take 3 next
    neighbors = top ++ middle ++ bottom



-- misc helper functions

-- splitEvery 5 [1..10] => [[1,2,3,4,5], [6,7,8,9,10]]
splitEvery :: Int -> [a] -> [[a]]
splitEvery n [] = []
splitEvery n xs = (take n xs):(splitEvery n (drop n xs))

-- The complement to splitEvery. 
-- flatten [[1,2,3],[4,5,6],[7,8,9]] => [1,2,3,4,5,6,7,8,9]
flatten xs = foldl (++) [] xs

sleep n = threadDelay $ round $ n * 1000000



-- The main event
main = do
  args <- getArgs
  let n = read (args !! 1) :: Int
      delay = if (length args) >= 3 then read (args !! 2) :: Float else 0.1
    in test (head args) n delay

test filename n delay = 
  do
    f <- openFile filename ReadMode
    contents <- hGetContents f
    let board = makeBoardFromStrings $ filter (\x -> (length x) == n) $ splitEvery n contents
        loop [] = putStrLn ""
        loop (b:bs) = 
          do
            (putStrLn . showBoard) b
            sleep delay
            loop bs
      in loop $ generations board 
          

```

---

### Post by dv3500ea on 2010-11-11
Here is a ruby game of life program. It is slightly prettier if you run it with ruby1.9.

```

class Array
	def resize! l
		l > length ?
			(l - length).times { push nil } :
			(length - l).times { pop }
		self
	end
	def resize l
		clone.resize! l
	end
	def group rows, columns
		resize(rows*columns).each_slice(columns).to_a
	end
	def group! rows, columns
		resize!(rows*columns).each_slice(columns).to_a
	end
end


class GameOfLife
	include Enumerable
	attr_accessor :grid, :rows, :columns
	def initialize str, rows, columns=nil
		if columns.nil?
			columns = rows
		end
		@rows = rows
		@columns = columns
		@grid = (str.gsub(/[^01]/, '').chars.map do |char|
			char == '1'
		end).group!(rows, columns)
	end
	#Find out whether or not a cell is alive
	def cell row, column
		row < 0 ? nil :
		row >= @rows ? nil :
		column < 0 ? nil :
		column >= @columns ? nil :
		@grid[row][column]
	end
	#list the neighbours of a cell
	def neighbours row, column
		[
			cell(row-1, column-1), #top left neighbour
			cell(row-1, column), #top neighbour
			cell(row-1, column+1), #top right neighbour
			cell(row, column-1), #left neighbour
			cell(row, column+1), #right neighbour
			cell(row+1, column-1), #bottom left neighbour
			cell(row+1, column), #bottom neighbour
			cell(row+1, column+1) #bottom right neighbour
		]
	end
	def each
		r = 0
		c = 0
		while r < @rows
			while c < @columns
				yield r, c
				c += 1
			end
			c = 0
			r += 1
		end
	end
	#excecute one iteration of the game of life
	def play_round
		#If I modify the current grid in place it doesn't work so I need to (deep) clone
		#the grid.
		newgrid = @grid.flatten.group(@rows, @columns)
		self.each do |r, c|
			alive_neighbours = (neighbours(r, c).select {|n| n}).count
			newgrid[r][c] = (if cell(r, c)
				if alive_neighbours < 2
					false #die
				elsif alive_neighbours > 3
					false #die
				else
					true #live
				end
			else
				if alive_neighbours == 3
					true #become alive!
				else
					false #stay dead :(
				end
			end)
		end
		@grid = newgrid
		self
	end
	#Find out if I can have the fancy boxes
	def ruby1_9?
		begin
			[].method 'enum_slice'
			false
		rescue
			true
		end
	end
	def to_s
		(@grid.map do |row|
			(row.map do |alive|
				#prettify if ruby1.9 (which has unicode support)
				alive ? (ruby1_9? ? "\u25FC" : '+') : (ruby1_9? ? "\u25FB" : '-')
			end).join ''
		end).join "\n"
	end
end

game = GameOfLife.new(
	File.open(ARGV[0]) { |f| f.read },
	ARGV[1].to_i,
	ARGV[2].nil? ? nil : ARGV[2].to_i
)

wait_time = ARGV[3] ? ARGV[3].to_f : 1.0

loop do
	puts game.play_round.to_s
	puts "\n\n"
	sleep wait_time
end

```

---

### Post by Some Penguin on 2010-11-11
Now that it's over, I'll upload my wacky Perl 5 code.

LifeGrid.pm:
   Module that handles all the computation.  It handles non-binary setups as well as toroidal maps.

driver.pl:
   Script which handles arguments and invokes the module.  It handles cycle detection, albeit expensively in terms of memory.

depretty.pl:
   Utility for taking a nicely formatted grid and turning it into an incomprehensible mess.


There's nothing particularly arcane in it -- I didn't go out of my way to use obscure Perl features.  It arguably does have some gratuitous automagic.

---

### Post by wkhasintha on 2010-11-11
OK I'm on it.. will do it in Java

---

