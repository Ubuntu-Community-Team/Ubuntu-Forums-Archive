---
title: "Perl+OpenGL(+Windows XP?) hemoraging memory"
date: 2008-06-03
forum: Programming Talk
---

### Post by Xyem on 2008-06-03
I'm trying to make a simple 2D game with Perl and OpenGL but even though I am only a tiny bit in ( ~70 lines ) Perl is eating memory like it is going out of fashion.

At first, it goes up by 1MB every few seconds. It seemed to "max out" at 160MB(!) before dropping back down to 60 where it started climbing again, albeit considerably slower.

I don't see what could be wrong, unless it is something to do with OpenGL.. I'm not using any complex structures or anything.

```
# Load pragmas
use strict;
use warnings;

# Load modules
use OpenGL qw	(	:glutfunctions :glutconstants
					:glfunctions :glconstants
					gluOrtho2D
				);

# Avoid globals
__PACKAGE__ -> new;

sub new
	{
	my $Self = bless {}, +shift;
	
	$Self -> initialise;
	glutMainLoop;
	}

sub initialise
	{
	my $Self = shift;
	
	# Initialise GLUT
	glutInit;
	glutInitDisplayMode ( GLUT_RGBA | GLUT_DOUBLE  );
	glutInitWindowPosition ( -1, -1 );
	glutInitWindowSize ( 320, 240 );
	glutCreateWindow ( 'BBOP' );
	glutDisplayFunc ( \&display, $Self );
	glutIdleFunc ( \&idle, $Self );
	glutKeyboardFunc ( \&keyboard, $Self );
	
	# Initialise view
	glMatrixMode ( GL_PROJECTION );
	glLoadIdentity;
	gluOrtho2D ( 0, 320, 0, 240 );
	glScalef ( 1, -1, 1 );
	glTranslatef ( 0, -240, 0 );
	glMatrixMode ( GL_MODELVIEW );
	}

sub display
	{
	my $Self = shift;
	
	glClear ( GL_COLOR_BUFFER_BIT );
	
	# Draw player
	glRecti ( 50, 50, 100, 100 );
	
	glutSwapBuffers;
	}

sub idle
	{
	my $Self = shift;
	
	glutPostRedisplay;
	}

sub keyboard
	{
	my $Self = shift;
	my ( $Char, $X, $Y ) = @_;
	
	if ( 27 == $Char )
		{ exit; }
	}
```

Can anyone spot ( or know ) what the problem is? If possible, I'd like to know if this happens on other machines or if it is this one specifically.

I don't want to continue if I am doing something fundamentally wrong so I would appreciate any feedback/information :)

---

