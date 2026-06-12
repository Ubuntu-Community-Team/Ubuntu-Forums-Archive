---
title: "GTK programming on Ubuntu5.10"
date: 2007-03-02
forum: Programming Talk
---

### Post by vk99 on 2007-03-02
Hi,

I've worked on C,C++,Java(Swing and JDBC) on microsoft windows as a part of my university coursework. I've recently installed Ubuntu5.10, I didn't install 6.06 as my computer has 256MD of RAM and thats the minimum required for 6.06(5.10 requires 128 min, I didnt want a slow system after insalling 6.06).

Ian using Anjuta1.2.4(its the only version that I've been able to get to work on Ubuntu5.10) for C/C++. I was reading SAMS Teach Yourself C for Linux Programming in 21 Days, theres a section on GUI programming using GTK. Iam trying to teach myself GTK...it sure has been a rough ride so far.

Here's the code that I am trying to compile
***********************************************************************
/*a minimal GTK+ program - its from SAMS Teach Yourself C for Linux Programming in 21 Days*/

#include <gtk-2.0/gtk/gtk.h>

void destroy_func(GtkWidget *widget,gpointer data);

int main(int argc,char*argv[])
{
	GtkWidget *main_win;
	gtk_init(&argc,&argv);
	main_win=gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_widget_set_usize(GTK_WIDGET(main_win),180,120);
	gtk_window_set_title(GTK_WINDOW(main_win),__FILE__);
	gtk_signal_connect(GTK_OBJECT(main_win),"destroy",
						GTK_SIGNAL_FUNC(destroy_func),NULL);
	/*make sure window is visible*/
	gtk_widget_show(main_win);
	gtk_main();
	g_print("About to exit main().\n");
	return 0;
}
void destroy_func(GtkWidget *widget,gpointer pdata)
{
	g_print("Quitting:Received destroy signal.\n");
	gtk_main_quit;
}
***********************************************************************

I have(among other things) gtk-2.0,glib-2.0,pango-1.0,atk-1.0,cairo in /usr/include, gtk2-engines(9 of them) are listed as installed in Synaptic, Synaptic also has libgtk 1.2, libgtk 1.2-common,libgtk 2.0,libgtk 2.0-bin,libgtk 2.0-common,libgtk 2.0-dev. However #include <gtk/gtk.h> gives me an error, saying that not such file or directory exists. I have tried using #include <gtk-2.0/gtk/gtk.h> instead but it gives me a long list of errors.
I have posted the complete list of errors here...srry its a long list, iam hoping it'll be of help to those reading the post...i think iam missing something here...like setting the path (using set path)on windows.
===========================================================================
In file included from list2101.c:3:
/usr/include/gtk-2.0/gtk/gtk.h:31:21: error: gdk/gdk.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:32:32: error: gtk/gtkaboutdialog.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:33:31: error: gtk/gtkaccelgroup.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:34:31: error: gtk/gtkaccellabel.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:35:29: error: gtk/gtkaccelmap.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:36:31: error: gtk/gtkaccessible.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:37:27: error: gtk/gtkaction.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:38:32: error: gtk/gtkactiongroup.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:39:31: error: gtk/gtkadjustment.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:40:30: error: gtk/gtkalignment.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:41:26: error: gtk/gtkarrow.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:42:32: error: gtk/gtkaspectframe.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:43:25: error: gtk/gtkbbox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:44:24: error: gtk/gtkbin.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:45:29: error: gtk/gtkbindings.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:46:24: error: gtk/gtkbox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:47:27: error: gtk/gtkbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:48:29: error: gtk/gtkcalendar.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:49:31: error: gtk/gtkcelllayout.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:50:33: error: gtk/gtkcellrenderer.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:51:38: error: gtk/gtkcellrenderercombo.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:52:39: error: gtk/gtkcellrendererpixbuf.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:53:41: error: gtk/gtkcellrendererprogress.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:54:37: error: gtk/gtkcellrenderertext.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:55:39: error: gtk/gtkcellrenderertoggle.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:56:29: error: gtk/gtkcellview.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:57:32: error: gtk/gtkcheckbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:58:34: error: gtk/gtkcheckmenuitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:59:30: error: gtk/gtkclipboard.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:60:26: error: gtk/gtkclist.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:61:32: error: gtk/gtkcolorbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:62:29: error: gtk/gtkcolorsel.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:63:35: error: gtk/gtkcolorseldialog.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:64:26: error: gtk/gtkcombo.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:65:29: error: gtk/gtkcombobox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:66:34: error: gtk/gtkcomboboxentry.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:67:30: error: gtk/gtkcontainer.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:68:26: error: gtk/gtkctree.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:69:26: error: gtk/gtkcurve.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:70:27: error: gtk/gtkdialog.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:71:24: error: gtk/gtkdnd.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:72:32: error: gtk/gtkdrawingarea.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:73:29: error: gtk/gtkeditable.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:74:26: error: gtk/gtkentry.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:75:36: error: gtk/gtkentrycompletion.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:76:26: error: gtk/gtkenums.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:77:29: error: gtk/gtkeventbox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:78:29: error: gtk/gtkexpander.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:79:28: error: gtk/gtkfilesel.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:80:26: error: gtk/gtkfixed.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:81:38: error: gtk/gtkfilechooserbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:82:38: error: gtk/gtkfilechooserdialog.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:83:38: error: gtk/gtkfilechooserwidget.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:84:31: error: gtk/gtkfontbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:85:28: error: gtk/gtkfontsel.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:86:26: error: gtk/gtkframe.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:87:26: error: gtk/gtkgamma.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:88:23: error: gtk/gtkgc.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:89:30: error: gtk/gtkhandlebox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:90:26: error: gtk/gtkhbbox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:91:25: error: gtk/gtkhbox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:92:27: error: gtk/gtkhpaned.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:93:27: error: gtk/gtkhruler.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:94:27: error: gtk/gtkhscale.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:95:31: error: gtk/gtkhscrollbar.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:96:31: error: gtk/gtkhseparator.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:97:32: error: gtk/gtkiconfactory.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:98:30: error: gtk/gtkicontheme.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:99:29: error: gtk/gtkiconview.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:100:26: error: gtk/gtkimage.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:101:34: error: gtk/gtkimagemenuitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:102:30: error: gtk/gtkimcontext.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:103:36: error: gtk/gtkimcontextsimple.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:104:35: error: gtk/gtkimmulticontext.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:105:32: error: gtk/gtkinputdialog.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:106:30: error: gtk/gtkinvisible.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:107:25: error: gtk/gtkitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:108:32: error: gtk/gtkitemfactory.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:109:26: error: gtk/gtklabel.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:110:27: error: gtk/gtklayout.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:111:25: error: gtk/gtklist.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:112:29: error: gtk/gtklistitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:113:30: error: gtk/gtkliststore.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:114:25: error: gtk/gtkmain.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:115:25: error: gtk/gtkmenu.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:116:28: error: gtk/gtkmenubar.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:117:29: error: gtk/gtkmenuitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:118:30: error: gtk/gtkmenushell.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:119:35: error: gtk/gtkmenutoolbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:120:34: error: gtk/gtkmessagedialog.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:121:25: error: gtk/gtkmisc.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:122:28: error: gtk/gtkmodules.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:123:29: error: gtk/gtknotebook.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:124:27: error: gtk/gtkobject.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:125:32: error: gtk/gtkoldeditable.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:126:31: error: gtk/gtkoptionmenu.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:127:26: error: gtk/gtkpaned.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:128:27: error: gtk/gtkpixmap.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:129:25: error: gtk/gtkplug.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:130:28: error: gtk/gtkpreview.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:131:29: error: gtk/gtkprogress.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:132:32: error: gtk/gtkprogressbar.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:133:32: error: gtk/gtkradioaction.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:134:32: error: gtk/gtkradiobutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:135:34: error: gtk/gtkradiomenuitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:136:36: error: gtk/gtkradiotoolbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:137:26: error: gtk/gtkrange.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:138:23: error: gtk/gtkrc.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:139:26: error: gtk/gtkruler.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:140:26: error: gtk/gtkscale.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:141:30: error: gtk/gtkscrollbar.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:142:35: error: gtk/gtkscrolledwindow.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:143:30: error: gtk/gtkselection.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:144:30: error: gtk/gtkseparator.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:145:38: error: gtk/gtkseparatormenuitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:146:38: error: gtk/gtkseparatortoolitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:147:29: error: gtk/gtksettings.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:148:27: error: gtk/gtksignal.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:149:30: error: gtk/gtksizegroup.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:150:27: error: gtk/gtksocket.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:151:31: error: gtk/gtkspinbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:152:30: error: gtk/gtkstatusbar.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:153:26: error: gtk/gtkstock.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:154:26: error: gtk/gtkstyle.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:155:26: error: gtk/gtktable.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:156:36: error: gtk/gtktearoffmenuitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:157:25: error: gtk/gtktext.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:158:31: error: gtk/gtktextbuffer.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:159:29: error: gtk/gtktextview.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:160:30: error: gtk/gtktipsquery.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:161:33: error: gtk/gtktoggleaction.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:162:33: error: gtk/gtktogglebutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:163:37: error: gtk/gtktoggletoolbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:164:28: error: gtk/gtktoolbar.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:166:31: error: gtk/gtktoolbutton.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:167:29: error: gtk/gtktoolitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:168:29: error: gtk/gtktooltips.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:169:25: error: gtk/gtktree.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:170:28: error: gtk/gtktreednd.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:171:29: error: gtk/gtktreeitem.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:172:30: error: gtk/gtktreemodel.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:173:36: error: gtk/gtktreemodelfilter.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:174:34: error: gtk/gtktreemodelsort.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:175:34: error: gtk/gtktreeselection.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:176:30: error: gtk/gtktreestore.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:177:29: error: gtk/gtktreeview.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:178:35: error: gtk/gtktreeviewcolumn.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:179:30: error: gtk/gtktypeutils.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:180:30: error: gtk/gtkuimanager.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:181:26: error: gtk/gtkvbbox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:182:25: error: gtk/gtkvbox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:183:28: error: gtk/gtkversion.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:184:29: error: gtk/gtkviewport.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:185:27: error: gtk/gtkvpaned.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:186:27: error: gtk/gtkvruler.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:187:27: error: gtk/gtkvscale.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:188:31: error: gtk/gtkvscrollbar.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:189:31: error: gtk/gtkvseparator.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:190:27: error: gtk/gtkwidget.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:191:27: error: gtk/gtkwindow.h: No such file or directory
list2101.c:5: error: syntax error before ‘*’ token
list2101.c: In function ‘main’:
list2101.c:9: error: ‘GtkWidget’ undeclared (first use in this function)
list2101.c:9: error: (Each undeclared identifier is reported only once
list2101.c:9: error: for each function it appears in.)
list2101.c:9: error: ‘main_win’ undeclared (first use in this function)
list2101.c:11: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
list2101.c:15: error: ‘NULL’ undeclared (first use in this function)
list2101.c: At top level:
list2101.c:22: error: syntax error before ‘*’ token
list2101.c: In function ‘destroy_func’:
list2101.c:25: error: ‘gtk_main_quit’ undeclared (first use in this function)
========================================================================


Hope someone knows how to fix this around here, hope Anjuta is the right IDE for working on GTK based apps. I am new to this,  trying to find my around linux :) 

Thanks

---

### Post by WW on 2007-03-02
Install **libgtk2.0-dev**.  You may also need other -dev packages; these are the packages that include the header files for the corresponding library.

---

### Post by lnostdal on 2007-03-02
i use this setup instead of anjuta:
[http://nostdal.org/~lars/writings/ubuntu-programming1.pdf](http://nostdal.org/~lars/writings/ubuntu-programming1.pdf)
[http://nostdal.org/~lars/writings/ubuntu-programming2.pdf](http://nostdal.org/~lars/writings/ubuntu-programming2.pdf)
[http://nostdal.org/~lars/writings/ubuntu-programming3.pdf](http://nostdal.org/~lars/writings/ubuntu-programming3.pdf) (this final part contains a howto get started with gtk+/glade)

but in general, regardless of ide/setup - you should use pkg-config to compile/link as shown in the last link above

edit: if glade-3 isn't available on breezy glade-2 will also work ..

---

### Post by vk99 on 2007-03-03
hi,

thanks everybody for helping out, I have managed to install glade 2.12.0
along with all the dependencies through synaptic. The program i was trying to run in my initial post now works. Thank you, Lars Nostdal, your tutorials were really helpful. I am using anjuta and then manually compiling the .c file using 
gcc -o file_name -Wall -g -std=c99 `pkg-config --cflags --libs gtk+-2.0`
file_name.c
below is code from inostdal's ubuntu-programming3.pdf...its not compiling...i have posted the error iam getting...looks like its having trouble recgnizing XML related function...how do i fix this???
=========================================================================
#define _GNU_SOURCE
#include<stdlib.h>
#include<gtk/gtk.h>
#include<libglade-2.0/glade/glade.h>   /*coz glade is in libglade-2.0 dir
and it doesnt recognize #include<glade/glade.h>*/

GtkSpinButton* spinbutton1;
GtkSpinButton* spinbutton2;
GtkLabel* label1;

void updateLabel(GtkWidget* widget,gpointer data)
{
	char* sum_str;
	asprintf(&sum_str, "%d",gtk_spin_button_get_value_as_int(spinbutton1)+gtk_spin_button_get_value_as_int(spinbutton2));
	gtk_label_set_text(label1,sum_str);
	free(sum_str);
	
}

int main(int argc,char* argv[],char* env[])
{
	GladeXML* xml;
	GtkWindow* window1;
	
	gtk_init(&argc,&argv);
	xml=glade_xml_new("/home/vikram/Projects/helloworld-glade/helloworld-glade.glade",NULL,NULL);
		
	window1=(GtkWindow*)glade_xml_get_widget(xml,"window1");
	spinbutton1=(GtkSpinButton*)glade_xml_get_widget(xml,"spinbutton1");
	spinbutton2=(GtkSpinButton*)glade_xml_get_widget(xml,"spinbutton2");
	label1=(GtkLabel*)glade_xml_get_widget(xml,"label1");
	
	g_signal_connect(G_OBJECT(spinbutton1),"value-changed",G_CALLBACK(updateLabel),NULL);
	g_signal_connect(G_OBJECT(spinbutton2),"value-changed",G_CALLBACK(updateLabel),NULL);
	g_signal_connect(G_OBJECT(window1),"destroy",G_CALLBACK(gtk_main_quit),NULL);
	
	updateLabel((GtkWidget*)spinbutton1,NULL);	//trigger initial update
	
	gtk_widget_show_all((GtkWidget*)window1);
	gtk_main();
	return 0;
}
=========================================================================
=========================================================================
vk99@ubuntu:~/Projects/helloworld-glade$ gcc -o helloworld-glade -Wall -g -std=c99 `pkg-config --cflags --libs gtk+-2.0` helloworld-glade.c
/tmp/cc7nrKht.o: In function `main':
/home/vikram/Projects/helloworld-glade/helloworld-glade.c:25: undefined reference to `glade_xml_new'
/home/vikram/Projects/helloworld-glade/helloworld-glade.c:27: undefined reference to `glade_xml_get_widget'
/home/vikram/Projects/helloworld-glade/helloworld-glade.c:28: undefined reference to `glade_xml_get_widget'
/home/vikram/Projects/helloworld-glade/helloworld-glade.c:29: undefined reference to `glade_xml_get_widget'
/home/vikram/Projects/helloworld-glade/helloworld-glade.c:30: undefined reference to `glade_xml_get_widget'
collect2: ld returned 1 exit status
=========================================================================
thanks again for helping out :)

---

### Post by lnostdal on 2007-03-03
try: 
```
gcc -o helloworld-glade -Wall -g -std=c99 `pkg-config --cflags --libs gtk+-2.0` `pkg-config --cflags --libs libglade-2.0` helloworld-glade.c
```

 ..the #include must be as in the pdf..

---

### Post by vk99 on 2007-03-03
Hi,

I changed the header to glade/glade.h and used the new command for compiling- it compiled but it doesnt run...
-------------------------------------------------------------------------------------------------------
vk99@ubuntu:~/Projects/helloworld-glade$ gcc -o helloworld-glade -Wall -g -std=c99 `pkg-config --cflags --libs gtk+-2.0` `pkg-config --cflags --libs libglade-2.0` helloworld-glade.c
vk99@ubuntu:~/Projects/helloworld-glade$ ./helloworld-glade

(helloworld-glade:7665): libglade-WARNING **: Expected <glade-interface>.  Got <GTK-Interface>.

(helloworld-glade:7665): libglade-WARNING **: did not finish in PARSER_FINISH state

(helloworld-glade:7665): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(helloworld-glade:7665): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(helloworld-glade:7665): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(helloworld-glade:7665): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(helloworld-glade:7665): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(helloworld-glade:7665): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(helloworld-glade:7665): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(helloworld-glade:7665): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(helloworld-glade:7665): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(helloworld-glade:7665): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(helloworld-glade:7665): Gtk-CRITICAL **: gtk_spin_button_get_value_as_int: assertion `GTK_IS_SPIN_BUTTON (spin_button)' failed

(helloworld-glade:7665): Gtk-CRITICAL **: gtk_spin_button_get_value_as_int: assertion `GTK_IS_SPIN_BUTTON (spin_button)' failed

(helloworld-glade:7665): Gtk-CRITICAL **: gtk_label_set_text: assertion `GTK_IS_LABEL (label)' failed

(helloworld-glade:7665): Gtk-CRITICAL **: gtk_widget_show_all: assertion `GTK_IS_WIDGET (widget)' failed
--------------------------------------------------------------------------------------------------------
thanks for helping out lnostdal, i think iam really close to getting this to work, what do i do next?

---

### Post by lnostdal on 2007-03-03
your .glade-file contains something that does not make sense:

```
(helloworld-glade:7665): libglade-WARNING **: Expected <glade-interface>. Got <GTK-Interface>.
```

the root of my .glade-file contains:
```

<glade-interface>

```

..while your contains as root:
```
<GTK-interface>
```

what glade are you using .. the 1.x one?  ....   start glade like this:  press alt-f2 type glade-3 then press enter ..  (edit: well, or at _least_ glade-2 .. but you should really upgrade ..)

---

### Post by vk99 on 2007-03-03
hi,

alt+F2 glade3 - no go
alt+F2 glade2 - no go
alt+F2 glade - brings up glade 0.6.4

under Applications>>Programming: i have two links to Glade:
one says Glade and points to Glade 0.6.4
The other says Glade Interface Builder points to Glade 2.12.0

under /usr/include i have both libglade-1.0 & libglade-2.0

i used glade 2.12.0 to create the GUI.

---

### Post by lnostdal on 2007-03-03
right .. try doing 
```
sudo aptitude install glade-2
```

edit: it's "glade-2" or "glade-3" .. not "glade2" or "glade3" ...

---

### Post by vk99 on 2007-03-04
hi,

i did sudo aptitude install glade-2
-------------------------------------------------------------------------------------------------
[I]Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done[/I]
-------------------------------------------------------------------------------------------------

so i downloaded glade3-3.0.0.tar.bz2 and did the sudo ./configure...sudo make...sudo make install routine. It installed itself. So right now i can alt+F2 to launch glade,glade-2 & glade-3.
Now, when i try the compilation code i get  a new error

-------------------------------------------------------------------------------------------------
[I]vk99@ubuntu:~/Projects/helloworld-glade$ gcc -o helloworld-glade -g -Wall -std=c99 `pkg-config --cflags --libs gtk+-2.0` `pkg-config --cflags --libs libglade-2.0` helloworld-glade.c
/usr/local/lib/libglade-2.0.so: undefined reference to `g_object_ref_sink'
collect2: ld returned 1 exit status
vk99@ubuntu:~/Projects/helloworld-glade$[/I]
-------------------------------------------------------------------------------------------------

i have tried reinstalling libglade a couple of time through synaptic...it didnt work...so i went ahead and downloaded libglade-2.6.0...did sudo ./configure...it worked without errors...however when i did sudo make i get the same undefined reference to `g_object_ref_sink' error

i am lost, i think i am something wrong here :(

---

### Post by lnostdal on 2007-03-04
[quote=vk99]
/usr/local/lib/libglade-2.0.so: undefined reference to `g_object_ref_sink'
[/quote]
that looks strange .. why is that file in the /usr/local/ -directory? or why does pkg-config refer to that file?

have you installed your own version of libglade or something? reason i'm asking is because stuff installed via ./configure && make && make install usually end up in /usr/local

this shows my setup, everything using ubuntu-packages:
```

lars@ibmr52:~/programming/lisp/swgtk$ pkg-config --list-all | grep glade
glade-sharp-2.0       Glade - Glade
libglade-2.0          Libglade - a library for dynamically loading GLADE interface files

lars@ibmr52:~/programming/lisp/swgtk$ pkg-config --libs libglade-2.0
-lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  

lars@ibmr52:~/programming/lisp/swgtk$ pkg-config --cflags libglade-2.0
-I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12  

lars@ibmr52:~/programming/lisp/swgtk$ locate libglade-2.0.so
/usr/lib/libglade-2.0.so.0
/usr/lib/libglade-2.0.so.0.0.7
/usr/lib/libglade-2.0.so

```

just upgrade to edgy and be done with it .. you'll find more updated packages there so you won't have to mess with this yourself

---

### Post by vk99 on 2007-03-04
hi,

I managed to lay my hands on a Dapper Drake installation CD - its installed now, cudnt find edgy.

Installed libglade-2.0,glade-2.0,libgtk-2.0... the whole bunch. Iam getting a little mad at myself coz after all this...it STILL doesnt work!

heres the latest list of errors :(
----------------------------------------------------------------------------------------
vk99@ubuntu:~/Projects/helloworld-glade$ gcc -o helloworld-glade -Wall -g -std=c99 `pkg-config --cflags --libs gtk+-2.0` `pkg-config --cflags --libs libglade-2.0` helloworld-glade.c
vk99@ubuntu:~/Projects/helloworld-glade$ ./helloworld-glade

(helloworld-glade:6507): Gdk-WARNING **: locale not supported by Xlib

(helloworld-glade:6507): Gdk-WARNING **: cannot set locale modifiers

(helloworld-glade:6507): libglade-WARNING **: Expected <glade-interface>.  Got <GTK-Interface>.

(helloworld-glade:6507): libglade-WARNING **: did not finish in PARSER_FINISH state

(helloworld-glade:6507): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(helloworld-glade:6507): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(helloworld-glade:6507): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(helloworld-glade:6507): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(helloworld-glade:6507): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(helloworld-glade:6507): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
(helloworld-glade:6507): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(helloworld-glade:6507): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
(helloworld-glade:6507): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(helloworld-glade:6507): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
(helloworld-glade:6507): Gtk-CRITICAL **: gtk_spin_button_get_value_as_int: assertion `GTK_IS_SPIN_BUTTON (spin_button)' failed

(helloworld-glade:6507): Gtk-CRITICAL **: gtk_spin_button_get_value_as_int: assertion `GTK_IS_SPIN_BUTTON (spin_button)' failed

(helloworld-glade:6507): Gtk-CRITICAL **: gtk_label_set_text: assertion `GTK_IS_LABEL (label)' failed

(helloworld-glade:6507): Gtk-CRITICAL **: gtk_widget_show_all: assertion `GTK_IS_WIDGET (widget)' failed

vk99@ubuntu:~/Projects/helloworld-glade$.
----------------------------------------------------------------------------------------

---

### Post by CrazyTn on 2007-03-05
Hello, 

I followed the 3 .pdf files instructions and installed everything.

typed in the codes, and tried to compile and got these errors and warning.
Can you tell me why?

The code is from the first example on the 3rd pdf

```
 gcc -o gtk-helloworld -Wall -g -std=c99 'pkg-config --cflags --libs gtk+-2.0' gtk-helloworld.c
gcc: pkg-config --cflags --libs gtk+-2.0: No such file or directory
gtk-helloworld.c:2:21: error: gtk/gtk.h: No such file or directory
gtk-helloworld.c:4: error: expected ‘)’ before ‘*’ token
gtk-helloworld.c: In function ‘main’:
gtk-helloworld.c:9: error: ‘GtkWidget’ undeclared (first use in this function)
gtk-helloworld.c:9: error: (Each undeclared identifier is reported only once
gtk-helloworld.c:9: error: for each function it appears in.)
gtk-helloworld.c:9: error: ‘window’ undeclared (first use in this function)
gtk-helloworld.c:10: error: ‘button’ undeclared (first use in this function)
gtk-helloworld.c:12: warning: implicit declaration of function ‘gtk_init’
gtk-helloworld.c:14: warning: implicit declaration of function ‘gtk_window_new’
gtk-helloworld.c:14: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
gtk-helloworld.c:15: warning: implicit declaration of function ‘gtk_button_new_with_lable’
gtk-helloworld.c:16: warning: implicit declaration of function ‘gtk_container_add’
gtk-helloworld.c:16: warning: implicit declaration of function ‘GTK_CONTAINER’
gtk-helloworld.c:18: warning: implicit declaration of function ‘g_signal_connect’
gtk-helloworld.c:18: warning: implicit declaration of function ‘G_OBJECT’
gtk-helloworld.c:19: warning: implicit declaration of function ‘G_CALLBACK’
gtk-helloworld.c:19: error: ‘hello’ undeclared (first use in this function)
gtk-helloworld.c:21: error: expected ‘)’ before ‘G_CALLBACK’
gtk-helloworld.c:22: warning: implicit declaration of function ‘gtk_widget_show_all’
gtk-helloworld.c:23: warning: implicit declaration of function ‘gtk_main’

```

---

### Post by lnostdal on 2007-03-05
CrazyTn:
you're using quote-characters:   '
what you need to use is back-quote:  `

like this:  `pkg-config --cflags --libs gtk+-2.0`

edit:
you can copy/paste directly from the text by highlighting using your mouse then middle-press (or press both-mouse buttons at once) in the console (or any destination)

---

### Post by lnostdal on 2007-03-05
vk99: 
you're still drawing the interface with an old version of glade .. or you're still using the old .glad-file

edit:
if you open your .glade-file in a text-editor you'll see that it contains <GTK-Interface> like described in the message:
(helloworld-glade:6507): libglade-WARNING **: Expected <glade-interface>. Got <GTK-Interface>.

here is the contents of my .glade-file:

```

<?xml version="1.0" standalone="no"?> <!--*- mode: xml -*-->
<!DOCTYPE glade-interface SYSTEM "http://glade.gnome.org/glade-2.0.dtd">

<glade-interface>

<widget class="GtkWindow" id="window1">
  <property name="visible">True</property>
  <property name="title" translatable="yes">window1</property>
  <property name="type">GTK_WINDOW_TOPLEVEL</property>
  <property name="window_position">GTK_WIN_POS_NONE</property>
  <property name="modal">False</property>
  <property name="resizable">True</property>
  <property name="destroy_with_parent">False</property>
  <property name="decorated">True</property>
  <property name="skip_taskbar_hint">False</property>
  <property name="skip_pager_hint">False</property>
  <property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
  <property name="gravity">GDK_GRAVITY_NORTH_WEST</property>
  <property name="focus_on_map">True</property>
  <property name="urgency_hint">False</property>

  <child>
    <widget class="GtkHBox" id="hbox1">
      <property name="visible">True</property>
      <property name="homogeneous">False</property>
      <property name="spacing">0</property>

      <child>
        <widget class="GtkSpinButton" id="spinbutton1">
          <property name="visible">True</property>
          <property name="can_focus">True</property>
          <property name="climb_rate">1</property>
          <property name="digits">0</property>
          <property name="numeric">False</property>
          <property name="update_policy">GTK_UPDATE_ALWAYS</property>
          <property name="snap_to_ticks">False</property>
          <property name="wrap">False</property>
          <property name="adjustment">1 0 100 1 10 10</property>
        </widget>
        <packing>
          <property name="padding">0</property>
          <property name="expand">True</property>
          <property name="fill">True</property>
        </packing>
      </child>

      <child>
        <widget class="GtkSpinButton" id="spinbutton2">
          <property name="visible">True</property>
          <property name="can_focus">True</property>
          <property name="climb_rate">1</property>
          <property name="digits">0</property>
          <property name="numeric">False</property>
          <property name="update_policy">GTK_UPDATE_ALWAYS</property>
          <property name="snap_to_ticks">False</property>
          <property name="wrap">False</property>
          <property name="adjustment">1 0 100 1 10 10</property>
        </widget>
        <packing>
          <property name="padding">0</property>
          <property name="expand">True</property>
          <property name="fill">True</property>
        </packing>
      </child>

      <child>
        <widget class="GtkLabel" id="label1">
          <property name="visible">True</property>
          <property name="label" translatable="yes">label1</property>
          <property name="use_underline">False</property>
          <property name="use_markup">False</property>
          <property name="justify">GTK_JUSTIFY_LEFT</property>
          <property name="wrap">False</property>
          <property name="selectable">False</property>
          <property name="xalign">0.5</property>
          <property name="yalign">0.5</property>
          <property name="xpad">0</property>
          <property name="ypad">0</property>
          <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
          <property name="width_chars">-1</property>
          <property name="single_line_mode">False</property>
          <property name="angle">0</property>
        </widget>
        <packing>
          <property name="padding">0</property>
          <property name="expand">False</property>
          <property name="fill">False</property>
        </packing>
      </child>
    </widget>
  </child>
</widget>

</glade-interface>

```

---

### Post by CrazyTn on 2007-03-05
> **lnostdal said:**
> CrazyTn:
you're using quote-characters:   '
what you need to use is back-quote:  `

like this:  `pkg-config --cflags --libs gtk+-2.0`

edit:
you can copy/paste directly from the text by highlighting using your mouse then middle-press (or press both-mouse buttons at once) in the console (or any destination)

lol I feel like a newbie.... I am so I guess that works out

Thanks

are there simpler ways to compile these programs?

---

### Post by CrazyTn on 2007-03-05
How would I compile without emacs?
Since I use vim

Is this the right script?

```
  1 dbg = Environment(CCFLAGS = '-g -Wall -std=c99',
  2                   CXXFLAGS = '-g -Wall)
  3 env = dbg
  4 gtkenv.Program('glade-helloworld', 'glade-helloworld.c')
  5 

```

---

### Post by lnostdal on 2007-03-05
you start the build-process by typing scons -u at the console .. no changes to the SConstruct-file is needed .. you can call scons -u from any editor; just define a shortcut key that executes it

what you've pasted is not what the complete SConstruct-file should look like though

---

### Post by vk99 on 2007-03-05
hi lnostdal ... thanks for being patient & sticking it out with me here :)
 it worked...i goofed up earlier...used the same old glade file...made a new glade file and it works like a dream :)

i get these warnings

(helloworld-glade:6507): Gdk-WARNING **: locale not supported by Xlib

(helloworld-glade:6507): Gdk-WARNING **: cannot set locale modifiers


any ideas why?

---

### Post by lnostdal on 2007-03-05
do you get the same messages when starting other GTK applications from the terminal?

try to start gedit from the terminal for instance

edit: 
i think i remember seeing this happen for GTK applications in general for both dapper and (early?) edgy

---

### Post by vk99 on 2007-03-05
yeah looks like it happend for all GTK apps...those warnings showed up fot Gedit.

---

### Post by CrazyTn on 2007-03-05
in the guide, 2nd pdf

dbg = Environment(CCFLAGS = '-g -Wall -std=c99',
                  CXXFLAGS = '-g -Wall)

missing a ' after g -Wall

---

### Post by CrazyTn on 2007-03-05
I am getting this error:

main.cpp:11: error: 'delete_event' was not declared in this scope
I checked to see if I have the file gtk.h and found it, so I dnt know what is causing it.

from
```
     g_signal_connect(G_OBJECT(mainWindow), "delete_event",
                     G_CALLBACK (delete_event), NULL);

```

I changed the above code to
```
     g_signal_connect(G_OBJECT(mainWindow), "destroy",
                      G_CALLBACK (destroy), NULL);

```
destroy is defined before the main method.

so is there a reason why the first code didnt work?

---

### Post by CrazyTn on 2007-03-05
silly me I didnt define delete_event

nm

---

### Post by lnostdal on 2007-03-06
> **CrazyTn said:**
> in the guide, 2nd pdf

dbg = Environment(CCFLAGS = '-g -Wall -std=c99',
                  CXXFLAGS = '-g -Wall)

missing a ' after g -Wall
thank you; this is corrected now

---

