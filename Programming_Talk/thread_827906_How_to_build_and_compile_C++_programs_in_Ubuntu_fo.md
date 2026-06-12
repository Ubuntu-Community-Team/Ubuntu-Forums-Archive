---
title: "How to build and compile C++ programs in Ubuntu for a Visual Studio user"
date: 2008-06-13
forum: Programming Talk
---

### Post by gluonman on 2008-06-13
Greetings, Linux programmers.
I am not new to C++ programming, but I am new to C++ programming in Linux. I'm used to writing C++ in the Visual Studio IDE and being able to push build and then compile so that the IDE runs the executable of my program, reporting any errors that may be in my code and pointing out where those errors are and how they should be fixed. However, I am now an exclusive Ubuntu user. I understand that the Ubuntu equivalent to Visual Studio's build/compile feature is a separate process from the writing of the code in a text editor of some sort. I've been recommended so many text editors, including Scite for an example, and Ubuntu IDEs like Eclipse, but I have been given no step-by-step instruction for how to take what code I've written and execute it as a compiled program. I've been told to run make, or do other such things. But you can't just tell a new Linux user to run make. What does it mean to run make? I need to know what program to run, how to run it, what syntax to use if it involves command line, etc. I just want to know how to run my programs.
Help, please.

---

### Post by LoneWolfJack on 2008-06-13
I have a little program here (written in C) that I wrote ages ago:

Put it in a new text file and run the following command on your shell:

```
gcc -Wall -g yourprogramname.c -o outputfilename `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
```

The run it by typing this on your shell:

```
./outputfilename
```

Like I said, it is a C program, but most C programs work with C++ as well and gcc can handle both, C and C++ so this should get you started.


```

#include <gtk/gtk.h>
#include <string.h>
#include <stdlib.h>

struct tictacstruct
	{
	char *user;
	GtkWidget *sbar;
	int context_id;
	char *TicTacToe;
	int button_id;
	int turn_id;
	};

char *my_itoa(int a,char *buffer, int buff_size)
	{
	char *temp;
	int b;
	temp = buffer;

	b = a;
	if(buffer == NULL)
		{return NULL;}

	while(a>0)
		{
		if(buff_size < 1)
			{return NULL;}
		b = a%10;
		*temp = b + '0' ;
		temp++;
		a = a/10;
		buff_size--;
		}
	*temp = '\0';
	return buffer;
	}

static char return_winner(char *tictactoe)
	{
	char *winner = ".";
	if(!strncmp(&tictactoe[0],"X",1) && !strncmp(&tictactoe[1],"X",1) && !strncmp(&tictactoe[2],"X",1))
		{winner = "X";}
	if(!strncmp(&tictactoe[3],"X",1) && !strncmp(&tictactoe[4],"X",1) && !strncmp(&tictactoe[5],"X",1))
		{winner = "X";}
	if(!strncmp(&tictactoe[6],"X",1) && !strncmp(&tictactoe[7],"X",1) && !strncmp(&tictactoe[8],"X",1))
		{winner = "X";}
	if(!strncmp(&tictactoe[0],"X",1) && !strncmp(&tictactoe[3],"X",1) && !strncmp(&tictactoe[6],"X",1))
		{winner = "X";}
	if(!strncmp(&tictactoe[1],"X",1) && !strncmp(&tictactoe[4],"X",1) && !strncmp(&tictactoe[7],"X",1))
		{winner = "X";}
	if(!strncmp(&tictactoe[2],"X",1) && !strncmp(&tictactoe[5],"X",1) && !strncmp(&tictactoe[8],"X",1))
		{winner = "X";}
	if(!strncmp(&tictactoe[0],"X",1) && !strncmp(&tictactoe[4],"X",1) && !strncmp(&tictactoe[8],"X",1))
		{winner = "X";}
	if(!strncmp(&tictactoe[2],"X",1) && !strncmp(&tictactoe[4],"X",1) && !strncmp(&tictactoe[6],"X",1))
		{winner = "X";}

	if(!strncmp(&tictactoe[0],"O",1) && !strncmp(&tictactoe[1],"O",1) && !strncmp(&tictactoe[2],"O",1))
		{winner = "O";}
	if(!strncmp(&tictactoe[3],"O",1) && !strncmp(&tictactoe[4],"O",1) && !strncmp(&tictactoe[5],"O",1))
		{winner = "O";}
	if(!strncmp(&tictactoe[6],"O",1) && !strncmp(&tictactoe[7],"O",1) && !strncmp(&tictactoe[8],"O",1))
		{winner = "O";}
	if(!strncmp(&tictactoe[0],"O",1) && !strncmp(&tictactoe[3],"O",1) && !strncmp(&tictactoe[6],"O",1))
		{winner = "O";}
	if(!strncmp(&tictactoe[1],"O",1) && !strncmp(&tictactoe[4],"O",1) && !strncmp(&tictactoe[7],"O",1))
		{winner = "O";}
	if(!strncmp(&tictactoe[2],"O",1) && !strncmp(&tictactoe[5],"O",1) && !strncmp(&tictactoe[8],"O",1))
		{winner = "O";}
	if(!strncmp(&tictactoe[0],"O",1) && !strncmp(&tictactoe[4],"O",1) && !strncmp(&tictactoe[8],"O",1))
		{winner = "O";}
	if(!strncmp(&tictactoe[2],"O",1) && !strncmp(&tictactoe[4],"O",1) && !strncmp(&tictactoe[6],"O",1))
		{winner = "O";}
	return *winner;
	}

static void tictac(GtkWidget *widget,struct tictacstruct *ttpass,int button_id)
	{
	char *output, *a, *b;
	char *c = " (turn ";
	char *d = ")";
	b = (char *)malloc(100);
	char winner = return_winner(ttpass->TicTacToe);

	if(!strncmp(gtk_button_get_label(GTK_BUTTON(widget))," ",1) && !strncmp(&winner,".",1))
		{
		if(!strncmp(ttpass->user,"X",1))
			{ttpass->user = "O";}
		else
			{ttpass->user = "X";}
		gtk_button_set_label(GTK_BUTTON(widget),ttpass->user);

		if(!strncmp(ttpass->user,"X",1))
			{
			a = "put an O ";
			b = my_itoa(ttpass->turn_id,b,100);
			output = (char *)calloc(strlen(a)+strlen(b)+strlen(c)+strlen(d)+1,sizeof(char));
			strcpy(output,a);
			strcat(output,c);
			strcat(output,b);
			strcat(output,d);
			gtk_statusbar_push(GTK_STATUSBAR(ttpass->sbar),ttpass->context_id,output);
			ttpass->TicTacToe[button_id] = 'X';
			}
		else
			{
			ttpass->turn_id = ttpass->turn_id+1;
			a = "put an X ";
			b = my_itoa(ttpass->turn_id,b,100);
			output = (char *)calloc(strlen(a)+strlen(b)+strlen(c)+strlen(d)+1,sizeof(char));
			strcpy(output,a);
			strcat(output,c);
			strcat(output,b);
			strcat(output,d);
			gtk_statusbar_push(GTK_STATUSBAR(ttpass->sbar),ttpass->context_id,output);
			ttpass->TicTacToe[button_id] = 'O';
			}

		winner = return_winner(ttpass->TicTacToe);

		if(!strncmp(&winner,"X",1))
			{gtk_statusbar_push(GTK_STATUSBAR(ttpass->sbar),ttpass->context_id,"Player X has won!");}
		if(!strncmp(&winner,"O",1))
			{gtk_statusbar_push(GTK_STATUSBAR(ttpass->sbar),ttpass->context_id,"Player O has won!");}

//		free(output);
		}

g_print("(tictac):  button_id: %i\n",button_id);
g_print("(tictac):  %c\n",ttpass->TicTacToe[0]);
g_print("(tictac):  %c\n",ttpass->TicTacToe[1]);
g_print("(tictac):  %c\n",ttpass->TicTacToe[2]);
g_print("(tictac):  %c\n",ttpass->TicTacToe[3]);
g_print("(tictac):  %c\n",ttpass->TicTacToe[5]);
g_print("(tictac):  %c\n",ttpass->TicTacToe[6]);
g_print("(tictac):  %c\n",ttpass->TicTacToe[7]);
g_print("(tictac):  %c\n",ttpass->TicTacToe[8]);

	}

static void tictac_1(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,0);}
static void tictac_2(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,1);}
static void tictac_3(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,2);}
static void tictac_4(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,3);}
static void tictac_5(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,4);}
static void tictac_6(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,5);}
static void tictac_7(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,6);}
static void tictac_8(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,7);}
static void tictac_9(GtkWidget *widget,struct tictacstruct *ttpass)
	{tictac(widget,ttpass,8);}

static gboolean delete_event(GtkWidget *widget,GdkEvent *event,gpointer data)
	{
	gtk_main_quit();
	return FALSE;
	}

int main(int argc, char *argv[])
	{
	GtkWidget *window;
	GtkWidget *button1, *button2, *button3, *button4, *button5, *button6, *button7, *button8, *button9;
	GtkWidget *box, *box_line1, *box_line2, *box_line3;
	GtkWidget *sbar;
	guint context_id;
	struct tictacstruct ttpass;
	char *user = "O";
	char TicTacToe[9] = {' ',' ',' ',' ',' ',' ',' ',' ',' '};
	
	gtk_init(&argc, &argv);
	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_window_set_title(GTK_WINDOW(window),"Tic Tac Toe");
	gtk_container_set_border_width(GTK_CONTAINER (window),10);

	sbar = gtk_statusbar_new();
	context_id = gtk_statusbar_get_context_id(GTK_STATUSBAR(sbar),"foo");
	gtk_statusbar_push(GTK_STATUSBAR(sbar),context_id,"put an X (turn 1)");
	ttpass.turn_id = 1;
	ttpass.user = user;
	ttpass.sbar = sbar;
	ttpass.context_id = context_id;
	ttpass.TicTacToe =& TicTacToe[0];

//g_print("(main): ttpass address %p\n",&ttpass);

	g_signal_connect(G_OBJECT(window),"delete_event",G_CALLBACK(delete_event),NULL);

	box = gtk_vbox_new(FALSE, 0);
	box_line1 = gtk_hbox_new(FALSE, 0);
	box_line2 = gtk_hbox_new(FALSE, 0);
	box_line3 = gtk_hbox_new(FALSE, 0);

	button1 = gtk_button_new_with_label(" ");
	button2 = gtk_button_new_with_label(" ");
	button3 = gtk_button_new_with_label(" ");
	button4 = gtk_button_new_with_label(" ");
	button5 = gtk_button_new_with_label(" ");
	button6 = gtk_button_new_with_label(" ");
	button7 = gtk_button_new_with_label(" ");
	button8 = gtk_button_new_with_label(" ");
	button9 = gtk_button_new_with_label(" ");

	gtk_box_pack_start(GTK_BOX(box_line1),button1,TRUE,TRUE,20);
	gtk_box_pack_start(GTK_BOX(box_line1),button2,TRUE,TRUE,20);
	gtk_box_pack_start(GTK_BOX(box_line1),button3,TRUE,TRUE,20);
	gtk_box_pack_start(GTK_BOX(box_line2),button4,TRUE,TRUE,20);
	gtk_box_pack_start(GTK_BOX(box_line2),button5,TRUE,TRUE,20);
	gtk_box_pack_start(GTK_BOX(box_line2),button6,TRUE,TRUE,20);
	gtk_box_pack_start(GTK_BOX(box_line3),button7,TRUE,TRUE,20);
	gtk_box_pack_start(GTK_BOX(box_line3),button8,TRUE,TRUE,20);
	gtk_box_pack_start(GTK_BOX(box_line3),button9,TRUE,TRUE,20);

	gtk_box_pack_start(GTK_BOX(box),box_line1,TRUE,TRUE,0);
	gtk_box_pack_start(GTK_BOX(box),box_line2,TRUE,TRUE,0);
	gtk_box_pack_start(GTK_BOX(box),box_line3,TRUE,TRUE,0);
	gtk_box_pack_start(GTK_BOX(box),sbar,TRUE,TRUE,0);

	gtk_container_add(GTK_CONTAINER (window),box);

	g_signal_connect(G_OBJECT(button1),"clicked",G_CALLBACK(tictac_1),&ttpass);
	g_signal_connect(G_OBJECT(button2),"clicked",G_CALLBACK(tictac_2),&ttpass);
	g_signal_connect(G_OBJECT(button3),"clicked",G_CALLBACK(tictac_3),&ttpass);
	g_signal_connect(G_OBJECT(button4),"clicked",G_CALLBACK(tictac_4),&ttpass);
	g_signal_connect(G_OBJECT(button5),"clicked",G_CALLBACK(tictac_5),&ttpass);
	g_signal_connect(G_OBJECT(button6),"clicked",G_CALLBACK(tictac_6),&ttpass);
	g_signal_connect(G_OBJECT(button7),"clicked",G_CALLBACK(tictac_7),&ttpass);
	g_signal_connect(G_OBJECT(button8),"clicked",G_CALLBACK(tictac_8),&ttpass);
	g_signal_connect(G_OBJECT(button9),"clicked",G_CALLBACK(tictac_9),&ttpass);

	gtk_widget_show_all(window);

	gtk_main();
	return 0;
	}

```

---

### Post by doorman on 2008-06-13
Maybe you should start with an IDE like Code::Blocks ( [http://www.codeblocks.org]("http://www.codeblocks.org/") ) which has integrated support for building & running programs ( through gcc & make ). Afterwards, you can start studying the code::blocks output, and start looking the man and/or web pages of given programs to clarify the usage and arguments of each one of them...

Sorry, you said in your post that a lot of people already pointed out a few editors, but, in my humble opinion, to explain all the arguments and variants of gcc / make is a hell of a job. If you want to know the syntax and purpose of each one of them, i suggest typing
```
$ man gcc
$ man make

```
in a termnal. This is a good starting point. That way, you can start compiling code and learning the important stuff ;)

btw, be aware that there are certain differences between gnu C++ and Windows C++, so if you get an error like "strcmpi: function not defined", don't be confused, but find the gnu function that performs the same task ( strcasecmp in this case )

---

### Post by dtmilano on 2008-06-13
<flame-war action="ignore">
Netbeans, the only IDE you need (see [features]("http://www.netbeans.org/features/index.html")).
</flmae-war>

---

### Post by KingTermite on 2008-06-13
Before a war is started, there are many IDEs in Linux, so do some analysis and choose one.  

This web page may be a starting point:
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments)

Also, the "old school" way is to use make files. It's probably still the way in which you have the most control. You can create make files in Visual Studio too, I've done it. Linux make files are probably more comprehensive and organized though. They set up rules for compiling, which flags, which preprocessor definitions, which libraries to use, where to search for additional libraries and header files. Basically all the same stuff you'd fine in your project settings in Visual Studio.

Make Wikipedia: [http://en.wikipedia.org/wiki/Make_file](http://en.wikipedia.org/wiki/Make_file)
Make manual (Gnu website): [http://www.gnu.org/software/make/manual/](http://www.gnu.org/software/make/manual/)


I'm just like you....my normal real is Visual Studio and I'm just beginning to jump in to some Linux programming. The next decision you will  have to make is which toolkit to use for GUI development. There are many of those too.

---

### Post by Zugzwang on 2008-06-13
I think that most of the comments here so far are quite misleading.

I can understand gluonman's confusion. There is clearly a need for good tutorials for people just like him/her. The point is that looking at the man page of "make" wouldn't help you much. It doesn't tell you how to compile programs. 

Make people here say that there's a need to look behind the scenes, something that Visual Studio users didn't do before. But there's a good reason why they didn't: There was no need to. Everything important can be found in the GUI. This is also the reason why these people often mix IDE and compilers. There's no real need to distinguish.

Even when using IDEs and such, then coding in Linux you still need to know the tools and what they do. Take the IDE KDevelop for example. When starting a new project, it will ask you what kind of project you want to make. You've got the choice between "Custom makefile", "CMake", "Automake" and so on. But how the hell should you know? 

The same applies to Code::Blocks, which I tried recently. Compiling might work well, but when it comes to including libraries, the thing was a mess. I remember good old Borland days - Just drag the library file into the project, add the include path to the settings and you were done. It's the same here as well, but the settings are very well hidden.

Also, tutorials become outdated quite soon or are unusable for beginners because they don't work. I tried a QT4 tutorial recently but the stuff just didn't want to compile. That was because "qmake" defaulted to "qmake-qt3". However, you couldn't see that from the error messages.

So what we really need is a GOOD wikibook/sticky or so for movers from Visual Studio or such IDEs to the Ubuntu (and Linux in general world) that needs to be maintained in order to deal with every problem that occur, that totally start from scratch as far as tools and the whole toolchain and libraries are concerned and that answer typical problems at the same time.

The advice given in this forum is often not too usable (I hereby declare that I'm no exception myself) as they often answer slightly different questions. LoneWolfJack's post is a nice example: It clearly shows how to compile a program using no IDE at all, but I don't think that the OP will understand the line:
```

gcc -Wall -g yourprogramname.c -o outputfilename `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`

```
So it is a nice hands-on example but doesn't tell the OP how things work. It's also quite likely that the thing won't work because of the missing "gtk-dev" (or whatever) packages on the OP's computer (LoneWolfJack, this is really not meant to be rude, it is just an example of *many* in this forum and yours is actually one of the better ones - also note that this post won't help him/her either).

So who would participate in such a project? I am aware of Laroza's wiki but that's not a all-in-one-place resource and searching the web for information is always a problem (for the reason see above).

---

### Post by LoneWolfJack on 2008-06-13
No offense taken. In fact, back when I tried to compile my first GTK program I was pretty annoyed that it just wouldn't work - until I figured out what packages to install and that I have to tell gcc where to find the libs.

Yet I suppose someone with programming knowledge and willingness to use linux will start fiddling with the solution given and eventually will understand what the command does en detail.

Also, you said yourself that understanding the internals of the IDEs isn't really necessary, so my question is, is understanding the gcc command? 

I agree, however, that a "programming under linux for ex-Visuals" may be a good idea - start a post and I'll be happy to try to correct you where necessary. Yet I never used an IDE and probably never will, so I wouldn't be a great help in writing a tutorial on how to deal with them under linux...

---

### Post by nvteighen on 2008-06-13
> **LoneWolfJack said:**
> 
I agree, however, that a "programming under linux for ex-Visuals" may be a good idea - start a post and I'll be happy to try to correct you where necessary. Yet I never used an IDE and probably never will, so I wouldn't be a great help in writing a tutorial on how to deal with them under linux...

I think lost something. Is the tutorial idea meant to help ex-Visuals migrate to Linux-IDE's or to help them abandon IDE's at all?

If it's the second, I may possibly help a bit as I'm also an ex-Visual (though pre-.NET).

---

### Post by gluonman on 2008-06-13
Thank you all for your help and your guidance. Given the information, I'm getting to comfortably programming in Linux. Thank you.

---

### Post by descendency on 2008-06-13
in terminal:
```
sudo apt-get install g++
```

Create a file (.cpp) then, in terminal (in the directory of the file):
```
g++ file.cpp -o code
./code
```

edit: I use geany for text editing. I don't really care much for an "IDE". I prefer to use the terminal compiler. 
Just incase you don't know, "cd Directory" changes your directory. To move backwards "cd .."

---

### Post by Mickeysofine1972 on 2008-06-15
If you want to develop using an IDE I recommend Code::Blocks which is available for linux and windows and has a similar layout and build button system to Visual studio and also has debugger and watches.

[http://www.codeblocks.org/](http://www.codeblocks.org/)

Mike

---

