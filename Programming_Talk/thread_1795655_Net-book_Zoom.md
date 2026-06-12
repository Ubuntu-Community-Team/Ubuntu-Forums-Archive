---
title: "Net-book Zoom"
date: 2011-07-03
forum: Programming Talk
---

### Post by Sisophon2001 on 2011-07-03
This morning I wrote a simple little program in FreeBASIC to zoom-out the display of my net-book (running UNR) when I need to access controls on a dialog box that is too big for the tiny display.

I think a utility like this (written in a main stream programming language) should be included in all net-book releases.

This is the full source code except the icon. Or you can get the lot from my web site. [weekendcode]("http://weekendcode.phatcode.net/")

Garvan

```
''GNU 2 or later
#include once "gtk/gtk.bi"
#include once "vbcompat.bi"
#include once "nr_res.bi"		'' icon resource
#define NULL 0


type globaldata
	connected as string
	currentzoom as double
end type

dim shared gd as globaldata

declare function menuitem_zoom_out cdecl(byval widget as GtkWidget ptr, byval event as GdkEvent, _
		byval user_data as gpointer) as integer
declare function menuitem_zoom_100 cdecl(byval widget as GtkWidget ptr, byval event as GdkEvent, _
		byval user_data as gpointer) as integer
declare function menuitem_zoom_in cdecl(byval widget as GtkWidget ptr, byval event as GdkEvent, _
		byval user_data as gpointer) as integer
declare function init() as integer

''------------------------------------------------------------------------------
''
'' Function:	main()
''
''------------------------------------------------------------------------------

	dim as GtkWidget ptr win
	dim as GtkWidget ptr vbox1
	dim as GtkToolbar ptr zoom_tools
	dim as GdkPixbuf ptr pixbuf
	
	'' initialize Gtk
	gtk_init( NULL, NULL )

	'' create a window
	win = gtk_window_new( GTK_WINDOW_TOPLEVEL )
	gtk_window_set_title( GTK_WINDOW(win), "ZOOM NETBOOK" )
	gtk_window_set_policy (GTK_WINDOW (win), FALSE, FALSE, TRUE)   ''fixed border
	gtk_window_set_position(GTK_WINDOW(win), GTK_WIN_POS_CENTER_ALWAYS)
	
	pixbuf = gdk_pixbuf_new_from_xpm_data(@xpm_icon(0))
	if pixbuf <> NULL then gtk_window_set_icon(GTK_WINDOW(win), pixbuf)
	
	'' create a vertical box (vbox) with a 10 pixel border
	vbox1 = gtk_vbox_new (FALSE, 10)
	
	'' rest of GUI
	gtk_container_set_border_width (GTK_CONTAINER (vbox1), 10)

	''snd toolbar
	zoom_tools = g_object_new(GTK_TYPE_TOOLBAR, NULL)
	gtk_toolbar_set_style(GTK_TOOLBAR (zoom_tools ), GTK_TOOLBAR_ICONS)
	gtk_container_set_border_width (GTK_CONTAINER (zoom_tools), 10)
	gtk_toolbar_insert_stock(zoom_tools, GTK_STOCK_ZOOM_OUT, "Zoom out", NULL, _
		GTK_SIGNAL_FUNC (@menuitem_zoom_out), NULL, -1)
	gtk_toolbar_insert_stock(zoom_tools, GTK_STOCK_ZOOM_100, "Zoom 1:1", NULL, _
		GTK_SIGNAL_FUNC (@menuitem_zoom_100), NULL, -1)
	gtk_toolbar_insert_stock(zoom_tools, GTK_STOCK_ZOOM_IN, "Zoom in", NULL, _
		GTK_SIGNAL_FUNC (@menuitem_zoom_in), NULL, -1)
	gtk_toolbar_insert_stock(zoom_tools, GTK_STOCK_QUIT, "Quit", NULL, _
		G_CALLBACK (@gtk_main_quit), NULL, -1)


	gtk_container_add (GTK_CONTAINER (vbox1), GTK_WIDGET(zoom_tools))
	

	gtk_container_add( GTK_CONTAINER(win), vbox1 )
	
	'' attach signals to widgets
	g_signal_connect (G_OBJECT (win), "destroy", G_CALLBACK (@gtk_main_quit), NULL)
	g_signal_connect (G_OBJECT (win), "delete_event", G_CALLBACK (@gtk_main_quit), NULL)
	
	'' Show GUI
	gtk_widget_show_all( win )
	''
	if init() = false then print "Call to xrandr failed"
	
	' Enter the event loop
	gtk_main ()


'' Purpose:		Zoom Out
function menuitem_zoom_out cdecl(byval widget as GtkWidget ptr, byval event as GdkEvent, _
		byval user_data as gpointer) as integer
	if gd.connected = "" then return 0
	gd.currentzoom *= 1.1
	return exec("xrandr", "--output " & gd.connected & " --scale " & str(gd.currentzoom) & "x" & str(gd.currentzoom))
end function

'' Purpose:		Zoom 100
function menuitem_zoom_100 cdecl(byval widget as GtkWidget ptr, byval event as GdkEvent, _
		byval user_data as gpointer) as integer
	if gd.connected = "" then return 0
	gd.currentzoom = 1
	return exec("xrandr", "--output " & gd.connected & " --scale 1.0x1.0")
end function

'' Purpose:		Zoom In
function menuitem_zoom_in cdecl(byval widget as GtkWidget ptr, byval event as GdkEvent, _
		byval user_data as gpointer) as integer
	if gd.connected = "" then return 0
	gd.currentzoom /= 1.1
	return exec("xrandr", "--output " & gd.connected & " --scale " & str(gd.currentzoom) & "x" & str(gd.currentzoom))
end function

'' Make sure we can find the connected video name 
function init() as integer
	dim as integer f1
	dim as string ln, vid
	
	gd.currentzoom = 1
	
	f1 = freefile
	if (open pipe("xrandr -q", for input, as #f1)) then
		print "couldn't run xrandr"
		return 0
	end if

	do until (eof(f1))
		line input #f1, ln
		if (len(ln) > 0) then
			if instr(ln, " connected") then
				vid = left(ln, instr(ln, " connected")-1)
				if len(vid) then gd.connected = vid
			end if
		end if
	loop
	close #f1

	if len(vid) then return true else return false
end function
```

---

