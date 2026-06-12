---
title: "Programming Challenge 5: Sierpinski's Triangle"
date: 2008-03-21
forum: Programming Talk
---

### Post by Lux Perpetua on 2008-03-21
Your task: write a program that draws [Sierpinski's triangle](http://mathworld.wolfram.com/SierpinskiSieve.html). Briefly: start with a solid triangle. The line segments connecting the midpoints of the three edges divide the original triangle into four smaller triangles. Take out the middle one, and repeat this process ad infinitum on the three remaining smaller triangles.

There are many ways to implement it, not all of which are mentioned on the MathWorld page. The word "draw" can be interpreted loosely: you could output an image, draw to a window, etc.  Bonus points will be given for creativity, both in choice of algorithm and in implementation of that algorithm. 

The deadline for entries is next Friday, March 28, let's say 5 PM EDT. I'll try to be available then to judge the submissions, but there's a chance I won't be, in which case we'll need another way to select the winner. Maybe the entrants can vote on it. I know that isn't ideal, but the show must go on. 

Have fun!

---

### Post by Wybiral on 2008-03-21
[I don't want to reduce other peoples options so I removed this one in case someone wanted to submit something similar]

---

### Post by Wybiral on 2008-03-21
UPDATE!

I think this is my final implementation :) This one is sort-of like a flight simulator with a big 3d Sierpinski Pyramid in the middle (if you complain that it's not a triangle, just look at one of the sides, it's multiple triangles!)

You need pygame and pyopengl.

```

import math
import pygame
from OpenGL.GL import *
from OpenGL.GLU import *
import random


def cosd(deg):
    return  math.cos(deg * 0.0174532925)

def sind(deg):
    return  math.sin(deg * 0.0174532925)

def sierpinski(p, depth):
    if not depth:
        glBegin(GL_TRIANGLE_FAN)
        for i in (0, 3, 2, 1, 3):
            glVertex3f(p[i].x, p[i].y, p[i].z)
        glEnd()
        glBegin(GL_TRIANGLES)
        for i in (1, 2, 3):
            glVertex3f(p[i].x, p[i].y, p[i].z)
        glEnd()
    else:
        depth -= 1
        points = ((0, 1), (0, 2), (0, 3), (1, 3), (3, 2), (2, 1))
        mid = [(p[a] + p[b]) * 0.5 for a, b, in points]
        sierpinski((p[0], mid[0], mid[1], mid[2]), depth)
        sierpinski((mid[0], mid[3], p[1], mid[5]), depth)
        sierpinski((mid[1], mid[5], p[2], mid[4]), depth)
        sierpinski((mid[2], mid[4], p[3], mid[3]), depth)


class Vec3d:

    def __init__(self, x=0.0, y=0.0, z=0.0):
        self.x, self.y, self.z = x, y, z

    def rotate_x(self, ang):
        s, c = sind(-ang), cosd(-ang)
        self.y, self.z = self.y * c + self.z * s, self.y * -s + self.z * c

    def rotate_y(self, ang):
        s, c = sind(-ang), cosd(-ang)
        self.x, self.z = self.x * c + self.z * -s, self.x * s + self.z * c

    def __add__(self, other):
        return Vec3d(self.x+other.x, self.y+other.y, self.z+other.z)

    def __mul__(self, scale):
        return Vec3d(self.x*scale, self.y*scale, self.z*scale)

    def length(self):
        return (self.x ** 2 + self.y ** 2 + self.z ** 2) ** 0.5


class Game:

    def __init__(self, width, height):
        pygame.init()
        disp = pygame.display
        disp.set_mode((width, height), pygame.DOUBLEBUF | pygame.OPENGL)
        glViewport(0, 0, width, height)
        glMatrixMode(GL_PROJECTION)
        gluPerspective(60, float(width) / height, 0.01, 6000)

        glMatrixMode(GL_MODELVIEW)
        glEnable(GL_DEPTH_TEST)
        self.key = [False for i in xrange(512)]
        self.objects = []

    def add_object(self, obj):
        obj.game = self
        self.objects.append(obj)

    def events(self):
        for e in pygame.event.get():
            if e.type == pygame.QUIT:
                self.key[pygame.K_ESCAPE] = True
            elif e.type == pygame.KEYDOWN:
                self.key[e.key] = True
            elif e.type == pygame.KEYUP:
                self.key[e.key] = False
        return not self.key[pygame.K_ESCAPE]

    def inkey(self, key):
        return self.key[key]

    def onkey(self, key):
        if self.key[key]:
            self.key[key] = False
            return True
        return False

    def start(self):
        for obj in self.objects:
            obj.init()
        clock = pygame.time.Clock()
        while self.events():
            clock.tick(50)
            glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT)
            glLoadIdentity()
            for obj in self.objects:
                obj.update()
            for obj in self.objects:
                obj.render()
            pygame.display.flip()


class Camera:

    def __init__(self, x=0.0, y=0.0, z=0.0):
        self.pos = Vec3d(x, y, z)
        self.ang = Vec3d()
        self.vel = Vec3d()
        self.rot = Vec3d()

    def init(self):
        glFogf(GL_FOG_DENSITY, 1.0)
        glFogi(GL_FOG_MODE, GL_EXP)
        glEnable(GL_FOG)

    def update(self):
        mov = Vec3d()
        delta = self.vel.length() + 0.03
        if self.game.inkey(pygame.K_DOWN):
            self.rot.x -= delta
        elif self.game.inkey(pygame.K_UP):
            self.rot.x += delta
        if self.game.inkey(pygame.K_RIGHT):
            self.rot.y -= delta
        elif self.game.inkey(pygame.K_LEFT):
            self.rot.y += delta
        if self.game.inkey(pygame.K_w):
            mov.z -= 0.00015
        elif self.game.inkey(pygame.K_s):
            mov.z += 0.00015
        if self.game.inkey(pygame.K_PAGEDOWN):
            mov.y -= 0.00015
        elif self.game.inkey(pygame.K_PAGEUP):
            mov.y += 0.00015
        if self.game.inkey(pygame.K_a):
            mov.x -= 0.00015
        elif self.game.inkey(pygame.K_d):
            mov.x += 0.00015
        if self.game.onkey(pygame.K_f):
            pygame.display.toggle_fullscreen()
        self.ang += self.rot
        mov.rotate_x(self.ang.x)
        mov.rotate_y(self.ang.y)
        self.vel += mov
        self.pos += self.vel
        self.vel *= 0.988
        self.rot *= 0.988

    def render(self):
        glRotatef(-self.ang.x, 1, 0, 0);
        glRotatef(-self.ang.y, 0, 1, 0);
        glTranslatef(-self.pos.x, -self.pos.y, -self.pos.z);


class Pyramid:

    def __init__(self, depth=1, max_depth=7):
        self.depth = depth
        self.max_depth = max_depth
        self.display_list = glGenLists(1)
        self.points = (Vec3d( 0.0,  1.0,  0.0), Vec3d( 1.0, -1.0, -1.0),
                       Vec3d( 0.0, -1.0,  1.0), Vec3d(-1.0, -1.0, -1.0))

    def build(self):
        pygame.display.set_caption("Calculating...")
        glNewList(self.display_list, GL_COMPILE)
        sierpinski(self.points, self.depth)
        glEndList()
        pygame.display.set_caption("Depth %i/%i" % (self.depth, self.max_depth))

    def init(self):
        glPolygonMode(GL_FRONT_AND_BACK, GL_LINE)
        self.build()

    def render(self):
        glCallList(self.display_list)

    def update(self):
        if self.game.onkey(pygame.K_SPACE):
            self.depth = (self.depth % self.max_depth) + 1
            self.build()


if __name__ == "__main__":
    game = Game(640, 480)
    game.add_object(Camera(0.0, 0.0, 2.0))
    game.add_object(Pyramid(7, 7))
    game.start()

```

Up / Down / Left / Right = control your rotation
W, S, A, D, PageUp, PageDown = control your thrust (motion)
Space = Toggle iteration depth

---

### Post by mike_g on 2008-03-21
I made this a while ago, so its fair enough if it dosent count. Its in Blitz Basic and draws a transforming/rotating Sierpinski triangle with pixel based color blending. For those of you w/o Blitz theres a screenie of it[ here.](http://i92.photobucket.com/albums/l15/mikegrundel/Lavapitdemo.jpg)

```
Dim palette2(512)
Dim sin_tab#(360)
Dim cos_tab#(360)

tri_pal=1: tri_inc=1
Global step_max = 5
Global rot, rot_inc=1
Global shift = 0, shift_inc = 2

Global tri_height = 150
Global tx1, ty1 
Global tx2, ty2
Global tx3, ty3


;PRECALC TABLES
For i=0 To 360
	sin_tab#(i)=Sin(i)
	cos_tab#(i)=Cos(i)
Next

r=0: g=0: b=0
For i = 0 To 512
	If b < 128
		b=b+1
	Else
		b=b-2
		r=r+1
	EndIf 
	palette2(i)=(r Shl 16)+b
Next

While Not KeyHit(1)
	Cls	
	count=count+2
	rot = rot + rot_inc
	If rot > 360 Then rot = rot - 360
	shift = shift + shift_inc
	If shift > 400 Or shift < -200 Then shift_inc = -shift_inc		
	tri_pal=tri_pal+tri_inc
	If tri_pal >= 150 Or tri_pal <= 0 Then tri_inc = -tri_inc
			
	LockBuffer
	Recuralateral(200, 200, 100, 0, tri_pal)
	UnlockBuffer		

	Flip 0
Wend 


Function Eqaulateral(cx, cy, rad, rot, steps, tri_pal)
	x1 = cx+(cos_tab#((0+rot) Mod 360)*rad)
	y1 = cy+(sin_tab#((0+rot) Mod 360)*rad)
	
	x2 = cx+(cos_tab#((120+rot) Mod 360)*rad)
	y2 = cy+(sin_tab#((120+rot) Mod 360)*rad)
	
	x3 = cx+(cos_tab#((240+rot) Mod 360)*rad)
	y3 = cy+(sin_tab#((240+rot) Mod 360)*rad)
	
	FilledTriangle(x1, y1, x2, y2, x3, y3, tri_pal, steps+1)
	
	Line x1, y1, x2, y2 
	Line x2, y2, x3, y3 
	Line x3, y3, x1, y1
	
End Function

Function Recuralateral(cx, cy, rad, steps, tri_pal)
	If steps = step_max Return 
	
	Color 255-(steps*50), 255-(steps*50), 255-(steps*50)
	
	
	Eqaulateral(cx, cy, rad, rot, steps, tri_pal)
	
	For i = 1 To 3
		x = cx+(cos_tab#((60+(i*120)+rot) Mod 360)*(rad+shift))
		y = cy+(sin_tab#((60+(i*120)+rot) Mod 360)*(rad+shift)) 
		rot = rot + 120
		If rot >= 360 Then rot = rot - 360
		Recuralateral(x, y, rad/2, steps+1, tri_pal)
	Next 
End Function

Function FilledTriangle(x1, y1, x2, y2, x3, y3, tcol, steps) 
		;opacity# = 0.5 / Float(steps*2)
		opacity = 150-(steps * 20) 
		
		LockBuffer 
		Local x[2] 
		Local y[2] 
		; First point is the highest 
		If y1 < y2 And y1 < y3 
			x[0] = x1 
			y[0] = y1 
			If y2 <= y3 
				x[1] = x2 
				y[1] = y2 
				x[2] = x3 
				y[2] = y3 
			Else 
				x[1] = x3 
				y[1] = y3 
				x[2] = x2 
				y[2] = y2 
			End If 
		Else 
		; Second point is the highest 
			If y2 < y1 And y2 < y3 
				x[0] = x2 
				y[0] = y2 
				If y1 <= y3  
					x[1] = x1 
					y[1] = y1 
					x[2] = x3 
					y[2] = y3 
				Else 
					x[1] = x3 
					y[1] = y3 
					x[2] = x1 
					y[2] = y1 	
				End If 
			; Third point is the highest 
			Else 
				x[0] = x3 
				y[0] = y3 
				If y1 < y2 
					x[1] = x1 
					y[1] = y1 
					x[2] = x2 
					y[2] = y2 
				Else 
					x[1] = x2 
					y[1] = y2 
					x[2] = x1 
					y[2] = y1 
				End If 
			End If 
		End If 
	lines# = y[1] - y[0] 
	tlines# = y[2] - y[0] 
	dx1# = x[2] - x[0] 
	dx2# = x[1] - x[0] 
	loop = lines - 1 
	loop2 = tlines - 1 
	; Go from highest point to second highest point, drawing horizontal lines only 
	For iy = 0 To loop 
		cy = y[0] + iy  
		start = x[0]+Floor((iy/tlines)*dx1)
		finish = x[0]+Floor((iy/lines)*dx2)
		
		If start > finish 
			temp = start
			start = finish
			finish = temp
		EndIf 		
		For xn = start To finish
			col2=ReadPixel(xn, cy)
			WritePixel(xn, cy, Blend2(palette2(tcol+iy), col2, opacity), BackBuffer())
		Next
	Next 
	dx2# = x[2] - x[1] 
	lines = y[2] - y[1] 
	loop = loop + 1 
	; Go from second highest point to lowest point, drawing horizontal lines only 
	For iy = loop To loop2 
		cy = y[0] + iy 
		start=x[0]+Floor((iy/tlines)*dx1)
		finish=x[1]+Floor(((iy-loop)/lines)*dx2)
		If start > finish 
			temp = start
			start = finish
			finish = temp
		EndIf
		For xn = start To finish
			 col2=ReadPixel(xn, cy)
			 WritePixel(xn, cy, Blend2(palette2(tcol+iy), col2, opacity), BackBuffer())
		Next
	Next 
	UnlockBuffer 
End Function

Function Blend2( rgb1, rgb2, alpha )
	alpha2 = 255-alpha
	r1 = (((rgb1 And $FF0000)Shr 8)*alpha2)And $FF0000
	g1 = ((rgb1 And $00FF00) * alpha) And $FF0000
	b1 = ((rgb1 And $0000FF) * alpha) ;And $0000FF00
	
	r2 = (((rgb2 And $FF0000)Shr 8)*alpha2)And $FF0000
	g2 = ((rgb2 And $00FF00) * alpha2) And $FF0000
	b2 = ((rgb2 And $0000FF) * alpha2) ;And $0000FF00	
	
	r3 = (r1+r2) And $FF0000
	g3 = (g1+g2) And $FF0000
	b3 = (b1+b2) And $00FF00
	Return r3 Or ((g3 Or b3)Shr 8)
End Function
```

---

### Post by Fbot1 on 2008-03-21
I'm go for the honorable mention for the abusing the rules:
```
program cheat;
begin
end.
```
doing infinite loops in less then a second.

---

### Post by Wybiral on 2008-03-23
Bumping the challenge...

---

### Post by LaRoza on 2008-03-23
> **Wybiral said:**
> Bumping the challenge...

Why? I have a feeling your solution is the best.

(That PyGame one is very good)

---

### Post by Wybiral on 2008-03-23
> **LaRoza said:**
> Why? I have a feeling your solution is the best.

(That PyGame one is very good)

mike_g's might be good but I don't have blitz (and it's like $80) so I can't tell. Regardless, me and mike_g need some competition and this is a pretty easy challenge plus an excuse to learn a 2d graphics library.

---

### Post by mike_g on 2008-03-23
The demo version is free, but only runs with the debugger on :( I have an executable version uploaded [here](http://dbfinteractive.com/index.php?PHPSESSID=1872017a0315bd4636088fe4a2e4c8d6&topic=2278.0) . I think it may have to be ran under WINE for Linux tho.

---

### Post by Lux Perpetua on 2008-03-24
> **Wybiral said:**
> ...This is a pretty easy challenge plus an excuse to learn a 2d graphics library.Yeah, that basically sums it up. :-) 

I hope you don't all think it's *too* easy, though. If you think it is, there are many methods out there for drawing this fractal, and chances are you haven't implemented all of them. (I definitely haven't, and I've programmed  many fractals.)

---

### Post by Wybiral on 2008-03-24
> **Lux Perpetua said:**
> Yeah, that basically sums it up. :-) 

I hope you don't all think it's *too* easy, though. If you think it is, there are many methods out there for drawing this fractal, and chances are you haven't implemented all of them. (I definitely haven't, and I've programmed  many fractals.)

That's true, but there are several implementations that are really simple to do. I have another one myself, but I'll wait until the challenge is over (I don't want to steal all the ideas).

---

### Post by Siph0n on 2008-03-24
I really wanna do this challenge, but work and my outside life is taking up all my time!!! :) I will try to get it done by tomorrow!

---

### Post by nick_h on 2008-03-24
Here is one written in Java using Pascal's Triangle mod 2 to generate the Sierpinski Triangle.  I have included controls to change the number of rows generated and the size of the smallest point plotted.

[php]import java.awt.*;
import java.awt.event.*;

import javax.swing.*;
import javax.swing.event.*;

/*
 * Displays a representation of Sierpinski Triangles
 * using the Pascal's Triangle mod 2 algorithm
 */
public class Sierpinski extends JFrame {
	
	private static final int WIDTH = 1200;
	private static final int HEIGHT = 600;
	private static final int DEFAULT_SIZE = 8;
	private static final int DEFAULT_SCALE = 1;
	
	PlotArea pa;
	JScrollPane sp;
	
	/*
	 * Constructor initialises the user interface
	 */
	public Sierpinski() {	
		super("Programming Challenge 5: Sierpinski Triangles");
		addWindowListener(new windowListener());

		JPanel tools, scaleSlider, sizeSlider;
		tools = new JPanel();
		scaleSlider = createSlider("Magnification:   X", "scale",
											1, 10, DEFAULT_SCALE);
		sizeSlider = createSlider("Size:   2**n where n =", "size",
											5, 12, DEFAULT_SIZE);
		tools.setLayout(new BoxLayout(tools, BoxLayout.LINE_AXIS));
		tools.add(scaleSlider);
		tools.add(sizeSlider);
		
		pa = new PlotArea();
		sp =  new JScrollPane(pa);
		sp.setPreferredSize(new Dimension(WIDTH, HEIGHT));

		Container contents = getContentPane();
		contents.add(tools, BorderLayout.SOUTH);
		contents.add(sp, BorderLayout.CENTER);

		this.pack();
		this.setVisible(true);
	}

	// Creates a panel containing a slider and its label
	private JPanel createSlider(String label, String name, 
									int min, int max, int interval) {
		JPanel p = new JPanel();
		JLabel l = new JLabel(label);
		JSlider s = new JSlider(min, max, interval);
		s.setPaintTicks(true);
		s.setPaintLabels(true);
		s.setMajorTickSpacing(1);
		s.setSnapToTicks(true);
		s.setName(name);
		s.addChangeListener(new changeListener());
		p.add(l);
		p.add(s);
		return p;
	}
	
	/*
	 * The main work is done here.
	 * Creates an array containing a Pascal's Triangle mod 2.
	 * Booleans are used to represent odd (true) and even (false) numbers.
	 * Since odd+odd=even even+even=even odd+even=odd even+odd=odd
	 * the result of adding ((a + b) mod 2) is just (a xor b) 
	 */
	public boolean[][] pascal(int n) {
		int i, j;
		boolean[][] pascal;
		boolean[] row = {true};
		pascal = new boolean[n][];
		pascal[0] = row;
		
		for (i=1; i<n; i++) {
			row = new boolean[i+1];
			row[0] = true; // Add initial 1 at start of row
			for (j=1; j<i; j++) {
				row[j] = pascal[i-1][j] ^ pascal[i-1][j-1];
			}
			row[j] = true; // Add final 1 at end of row
			pascal[i] = row;
		}
		return pascal;
	}
	
	/*
	 * This class handles the display.
	 * This Sierpinski Triangle is held in the boolean array coords.
	 */
	public class PlotArea extends JPanel {
		private boolean[][] coords;
		private int size;
		private int scale;
		
		// Constructors
		public PlotArea(int size, int scale) {
			this.size = size;
			this.scale = scale;
			this.coords = pascal(size);
			this.setPreferredSize(new Dimension(size*2*scale, size*scale));
		}
		public PlotArea() {
			this(1<<DEFAULT_SIZE, DEFAULT_SCALE);
		}
		
		// Functions to set size and scale
		public void setSize(int size) {
			this.size = size;
			this.coords = pascal(size);
			this.setPreferredSize(new Dimension(size*2*scale, size*scale));
		}
		public void setScale(int scale) {
			this.scale = scale;
			this.setPreferredSize(new Dimension(size*2*scale, size*scale));
		}
		
		/*
		 * This is where the Triangle is displayed
		 * Simply scan through the array and plot the true values
		 */
		protected void paintComponent(Graphics g) {
            super.paintComponent(g);
			g.setColor(new Color(0,0,255));
			g.translate(size * scale, 0);  // Move the origin to top-centre
			for (int x=0; x<size; x++)
				for (int y=0; y<coords[x].length; y++)
					if (coords[x][y])
						g.fillRect((y*2 - x)*scale, x*scale, scale, scale);
		}
	}
	
	// Listeners for the window and sliders
	public class windowListener extends WindowAdapter {
		public void windowClosing(WindowEvent e) {
			System.exit(0);
		}
	}
	public class changeListener implements ChangeListener {
		public void stateChanged(ChangeEvent e) {
			JSlider slider = (JSlider)e.getSource();
			if (slider.getName() == "size") {
				pa.setSize(1<<(int)slider.getValue());
			} else {
				pa.setScale((int)slider.getValue());
			}
			// This next bit resizes the display and centres
			// it when a slider is moved.
			pa.invalidate();
			sp.validate();
			JScrollBar hs = sp.getHorizontalScrollBar();
			JScrollBar vs = sp.getVerticalScrollBar();
			hs.setValue((hs.getMaximum()-sp.getWidth())/2);
			vs.setValue(0);
			pa.repaint();
		}
	}
	
	public static void main(String[] args) {
		new Sierpinski();
	}
}
[/php]

---

### Post by mike_g on 2008-03-24
Nice, I never knew you could draw it from Pascals Triangle :)

---

### Post by stratavarious on 2008-03-25
.

---

### Post by Wybiral on 2008-03-25
I updated my submission (I decided that 2d was too easy). [Here it is]("http://ubuntuforums.org/showpost.php?p=4558021").

---

### Post by nick_h on 2008-03-26
> The algorithm is implemented in C++ (compile it with g++)
Stratavarious - What libraries are needed to compile your code?
I installed libcairo2-dev and libgtk2.0-dev but got errors.

---

### Post by Lux Perpetua on 2008-03-26
It compiled for me: ```
g++ `pkg-config --libs --cflags gtk+-2.0` test.cpp
```(I saved the code to "test.cpp".) Without the pkg-config part, I guess the compiler doesn't look in the right directories for the header files.

---

### Post by LaRoza on 2008-03-26
> **Lux Perpetua said:**
> It compiled for me: ```
g++ `pkg-config --libs --cflags gtk+-2.0` test.cpp
```(I saved the code to "test.cpp".) Without the pkg-config part, I guess the compiler doesn't look in the right directories for the header files.

No, it won't link the program without that.

The cpp handles the includes.

---

### Post by Lux Perpetua on 2008-03-26
Here's the output of **pkg-config --cflags gtk+-2.0**: > -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12It's all header file directories. The preprocessor does handle include files, but it needs to know where to look for them.

---

### Post by nick_h on 2008-03-26
> **Lux Perpetua said:**
> It compiled for me: ```
g++ `pkg-config --libs --cflags gtk+-2.0` test.cpp
```(I saved the code to "test.cpp".) Without the pkg-config part, I guess the compiler doesn't look in the right directories for the header files.

Thanks, that got it working.  I was writing the -I flags myself (and missed some).

---

### Post by xelapond on 2008-03-27
Ill be trying this one in Python, but I don't know if I can finish it in time.  Sounds interesting though, and a good excuse to learn 2D graphics.

Alex

---

### Post by Lster on 2008-03-27
It's not quite finished yet - I aim to have it for tomorrow if possible! This is a quick screenshot of it's current status:

---

### Post by ae+ on 2008-03-27
ackkk

ever since reading this post this morning i couldn't get it out of my head :)

so, i left work alone and put together this with actionscript:
[PHP]class Sierpinski {

	static var app : Sierpinski;
	public var addDepth : Number = 5;
	
	
	// entry point
	static function main(mc) {
		app = new Sierpinski();
	}
	
	function Sierpinski() {

		// Make a base to make stuff in
		var base:MovieClip = _root.createEmptyMovieClip('base', this.addDepth++);
		var a = 400;
		this.make_sierpinski(base, a);

	}
	
	
	private function make_sierpinski(where:MovieClip, size:Number){
		
		var divider:Number = size / 8;
		var limiter:Number = 30;
		var line_style:Array;
		var t1:MovieClip, t2:MovieClip, t3:MovieClip;

		// Top triangle
		line_style = [1,0xF23E02,100];
		t1 = where.createEmptyMovieClip('t1_'+this.addDepth, this.addDepth++);
		t1._x = divider*3;
		t1._y = divider;
		this.make_triangle(t1,0,0,size/2,line_style);
		if(size>limiter){
			this.make_sierpinski(t1, size/2);
		}
		
		// Left bottom triangle
		line_style = [1,0x00988D,100];
		t2 = where.createEmptyMovieClip('t2_'+this.addDepth, this.addDepth++);
		t2._x = divider*1;
		t2._y = divider*4;
		this.make_triangle(t2,0,0,size/2,line_style);
		if(size>limiter){
			this.make_sierpinski(t2, size/2);
		}


		// Right bottom triangle
		line_style = [1,0x013750,100];
		t3 = where.createEmptyMovieClip('t3_'+this.addDepth, this.addDepth++);
		t3._x = divider*5;
		t3._y = divider*4;
		this.make_triangle(t3,0,0,size/2,line_style);
		if(size>limiter){
			this.make_sierpinski(t3, size/2);
		}
		
		
	}
	
	private function make_triangle(where:MovieClip,x:Number,y:Number,side:Number,line_style:Array){
		
		var quarter:Number = side /4;
		where.lineStyle(line_style[0], line_style[1], line_style[2]);
		//where.beginFill(line_style[1], line_style[2]);
		where.moveTo(x+quarter, y+side);
		where.lineTo(x+side-quarter, y+quarter);
		where.lineTo(x+side+quarter, y+side);
		where.lineTo(x+quarter, y+side);
		//where.endFill();
	}
}[/PHP]

To see this on ubuntu ::
sudo apt-get install mtasc  
save the above code into Sierpinski.as
then run this in the same directory as the above file.

mtasc -swf sierpinski.swf -main -header 800:600:20 Sierpinski.as && firefox sierpinski.swf

it should open it up in firefox

---

### Post by ibuclaw on 2008-03-27
HaHa!

Erm...
Until I figure out how to do complex maths and line printing in COBOL.

This will do. (It's terrible, I know) :lolflag:
I've just changed it to make it look less conspicuous. 
```

000100 IDENTIFICATION DIVISION.
000200 PROGRAM-ID. SIERPINSKI.
000300 ENVIRONMENT DIVISION.
000400 DATA DIVISION.
000500 
000600 WORKING-STORAGE SECTION.
000700 01 WAIT-FOR-INPUT PIC X.
000800 
000900 SCREEN SECTION.
001000 01 SIERPINSKI-TRIANGLE.
001100    05 BLANK SCREEN.
001200    05 LINE  1 COL 10 VALUE "".
001300    05 LINE  2 COL 26 VALUE ".".
001400    05 LINE  3 COL 25 VALUE ".o.".
001500    05 LINE  4 COL 24 VALUE ".   .".
001600    05 LINE  5 COL 23 VALUE ".o. .o.".
001700    05 LINE  6 COL 22 VALUE ".       .".
001800    05 LINE  7 COL 21 VALUE ".o.     .o.".
001900    05 LINE  8 COL 20 VALUE ".   .   .   .".
002000    05 LINE  9 COL 19 VALUE ".o. .o. .o. .o.".
002100    05 LINE 10 COL 18 VALUE ".               .".
002200    05 LINE 11 COL 17 VALUE ".o.             .o.".
002300    05 LINE 12 COL 16 VALUE ".   .           .   .".
002400    05 LINE 13 COL 15 VALUE ".o. .o.         .o. .o.".
002500    05 LINE 14 COL 14 VALUE ".       .       .       .".
002600    05 LINE 15 COL 13 VALUE ".o.     .o.     .o.     .o.".
002700    05 LINE 16 COL 12 VALUE ".   .   .   .   .   .   .   .".
002800    05 LINE 17 COL 11 VALUE ".o. .o. .o. .o. .o. .o. .o. .o.".
002900    05 LINE 18 COL 10 VALUE "".
003000 PROCEDURE DIVISION.
003100
003200 PROGRAM-BEGIN.
003300  DISPLAY SIERPINSKI-TRIANGLE.
003400  ACCEPT WAIT-FOR-INPUT.
003500  
003600 PROGRAM-EXIT.
003700  EXIT PROGRAM.
003800
003900 PROGRAM-DONE.
004000  STOP RUN.


```
To compile run
> 
cobc -x sierpinski.cbl
./sierpinski

Try and guess what the output is... 8)

Wybiral, that is an excellent program you made there.
I felt like I was in a game somewhere between Halo and Tron! :)

Regards
Iain

---

### Post by jpages on 2008-03-28
My little contribution, with Python and PyGTK :

```

#! /usr/bin/python

import pygtk
pygtk.require('2.0')
import gtk

N_REC_MAX = 5
BLUE = gtk.gdk.Color(0,0,255)
WHITE = gtk.gdk.Color(255,255,255)
GREEN = gtk.gdk.Color(0,255,0)

def sierpins(gc, new_points, n):
    #print "sierpins ", n
    gc.foreground = GREEN
    drawing_area.window.draw_polygon(gc,False,new_points)
    xa = new_points[0][0]
    ya = new_points[0][1]
    xb = new_points[1][0]
    yb = new_points[1][1]
    xc = new_points[2][0]
    yc = new_points[2][1]
    print xa, ya, xb, yb, xc, yc
    if n < N_REC_MAX:
        sierpins(gc,[(xa,ya),((xa+xb)/2,(ya+yb)/2),((xa+xc)/2,(ya+yc)/2)],n+1)
        sierpins(gc,[(xb,yb),((xa+xb)/2,(ya+yb)/2),((xb+xc)/2,(yb+yc)/2)],n+1)
        sierpins(gc,[(xc,yc),((xa+xc)/2,(ya+yc)/2),((xb+xc)/2,(yb+yc)/2)],n+1)

def draw_area(area,event):
    style = drawing_area.get_style()
    gc = style.fg_gc[gtk.STATE_NORMAL]
    gc.foreground = BLUE
    print gc.foreground.blue
    drawing_area.window.draw_polygon(gc,False,points)
    #drawing_area.window.draw_polygon(gc,False,points2)
    sierpins(gc, points,0)
        
if __name__ == "__main__":
    points = [(10,10),(350,10),(250,250)]
    points2 = [(50,50),(390,40),(260,280)]
    main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    drawing_area = gtk.DrawingArea()
    #print drawing_area.name
    drawing_area.set_size_request(400,400)
    drawing_area.connect("expose-event", draw_area)
    #print type(drawing_area), type(gc)
    main_window.add(drawing_area)
    main_window.show()
    drawing_area.show()
    gtk.main()

```

---

### Post by Lux Perpetua on 2008-03-29
Good job, everybody. After reading all the submissions and running a few of them, I have results:

[color=blue]***Winner***[/color]

**Wybiral**. Although its algorithm is not very special (straightforward recursion), Wybiral's program takes this challenge to the next level by rendering the 3D version of Sierpinski's triangle (which as noted includes Sierpinski's triangle on each face of the pyramid) and allowing the user to see it from all perspectives, including from the inside. Congratulations!

[color=green]***Honorable Mention***[/color]

**nick_h**. nick_h's program is not recursive at all, but uses the fact that Pascal's triangle mod 2 looks like Sierpinski's triangle. 

**stratavarious**. stratavarious's program is also nonrecursive. For each iteration, it just does a big loop to draw all the triangles on that level. To calculate the position of each triangle, it uses a simple formula involving the base 3 digits of the loop counter. Read the code for details. ;-)

Closing comments: 

- I had a hell of a time deciding between stratavarious and Wybiral. In the end, the bad formatting of stratavarious's code counted against it (sorry, but it counts), and the enjoyment of playing with Wybiral's program counted in its favor. 

- For other ways of drawing Sierpinski's triangle, look up "chaos game" (very surprising and cool) and "Sierpinski arrowhead" (sometimes just "Sierpinski curve"). An apparently nonserious early submission by Wybiral (since removed) showed a method I didn't know, which basically amounts to seeing which pairs of coordinates on a 2D grid have "1" bits in common when written in base 2. nick_h's Pascal's triangle algorithm generalizes slightly: it is an example of a 1D cellular automaton, and there are a few more that also draw Sierpinski's triangle. 

- In a discussion that was split off from this thread, someone noted that Sierpinski's triangle, since it has no area, can't actually be seen; this makes it unclear how to draw it accurately, since increasingly more "accurate" pictures would actually converge to a blank image. The way I usually get around this problem is with shading: the points of Sierpinski's triangle are still colored black, and the other points aren't black, but they aren't necessarily white, and I use the darkness to indicate how "close" in some sense that point is to the fractal itself (not literally, though one *could*). 

I look forward to the next challenge!

---

### Post by Lster on 2008-03-29
Congrats Wybiral! :) Looking forwards to the next challenge!

---

