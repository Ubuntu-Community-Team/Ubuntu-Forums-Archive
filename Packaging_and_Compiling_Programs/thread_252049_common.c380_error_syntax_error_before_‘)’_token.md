---
title: "common.c:380: error: syntax error before ‘)’ token"
date: 2006-09-06
forum: Packaging and Compiling Programs
---

### Post by %hMa@?b&lt;C on 2006-09-06
I have modified a GPL'd program (pv2tool) to remove some buttons and add functionality, but when i try to compile I get this error
```
common.c:380: error: syntax error before ‘)’ token
```
my common.c file is here, please help me fix the syntax error. Thanks.
```
#include "globals.h"

#include <stdio.h>
#include <stdlib.h>
#include <getopt.h>



//////////////////////////////////////////
// various true (multi-file) globals
//GtkWidget *main_window = NULL;
flash_file_info* root_directory;
gboolean toggle_camera_lcd_screen_is_on;
GtkWidget* m_directory_tree = NULL;


gboolean flipper_capture;
//int stopwatch;   //maybe time downloads in the future and printout a bitrate

GdkPixbuf* icon_blankdir;
GdkPixbuf* icon_avifile;
GdkPixbuf* icon_binfile;
GdkPixbuf* icon_jpgfile;
GdkPixbuf* icon_txtfile;
GdkPixbuf* icon_wavfile;
GdkPixbuf* icon_zbmfile;

extern const guint8 avifile[], binfile[], blankdir[], jpgfile[];
extern const guint8 txtfile[], wavfile[], zbmfile[];

static void load_file_icons(void) {
  icon_blankdir = gdk_pixbuf_new_from_inline(-1, blankdir, FALSE, NULL);

  icon_avifile = gdk_pixbuf_new_from_inline(-1, avifile, FALSE, NULL);
  icon_binfile = gdk_pixbuf_new_from_inline(-1, binfile, FALSE, NULL);
  icon_jpgfile = gdk_pixbuf_new_from_inline(-1, jpgfile, FALSE, NULL);
  icon_txtfile = gdk_pixbuf_new_from_inline(-1, txtfile, FALSE, NULL);
  icon_wavfile = gdk_pixbuf_new_from_inline(-1, wavfile, FALSE, NULL);
  icon_zbmfile = gdk_pixbuf_new_from_inline(-1, zbmfile, FALSE, NULL);
  
}


//////////////////////////////////////////

static GtkWidget *information_label;
  
typedef struct {
  GtkWidget* button_open_camera;
  GtkWidget* button_unlock_camera;
} button_set;

#define NUM_OF_BUTTONS ( sizeof(button_set) / sizeof(GtkWidget*) )

union button_union {
  button_set b_s;
  GtkWidget* buttons[NUM_OF_BUTTONS];
} b_u;

void create_and_display_button(void* func, const char* caption, GtkWidget* box, GtkWidget** button) {
  *button = gtk_button_new_with_label(caption);
  gtk_signal_connect (GTK_OBJECT (*button), "clicked",
		      GTK_SIGNAL_FUNC(func), NULL);

  gtk_box_pack_start (GTK_BOX (box), GTK_WIDGET(*button), TRUE, TRUE, 0);
}

#define create_and_display_button_short(func, caption, box) \
  create_and_display_button(func, caption, box, &( b_u.b_s.button_##func ));

static gboolean delete_event (GtkWidget * widget, GdkEvent * event, gpointer data)
{
  // quiet compiler
  widget=widget;
  event=event;
  data=data;

  return FALSE;
}


/* Another callback */
static void destroy (GtkWidget * widget, gpointer data)
{
  // quiet compiler
  widget=widget;
  data=data;

  gtk_main_quit ();
  
}

gboolean enable_buttons (GtkWidget* widget,
			 GdkEvent *event,
			 gpointer data) {
  // quiet compiler
  widget=widget;
  event=event;
  data=data;
  
  EnableControls(TRUE);
  return TRUE;

}




static void reset_label(GtkTreeView* treeview,
		 GtkTreePath *arg1,
		 GtkTreeViewColumn *arg2,
		 gpointer data_null) {
  GtkTreeSelection* selection;
  GtkTreeIter iter;
  GtkTreeModel* model;
  gpointer data;
  gchar* filename;
  char strfiletype[STRINGSIZE];
  // quiet compiler
  treeview=treeview;
  arg1=arg1;
  arg2=arg2;
  data_null=data_null;

  

  selection = gtk_tree_view_get_selection(GTK_TREE_VIEW(m_directory_tree));
  if (gtk_tree_selection_get_selected(selection, &model, &iter)) {
    char tempstring[STRINGSIZE];
    //    gpointer data = NULL;
    flash_file_info* p = NULL;
   
    gtk_tree_model_get (model, &iter, COL_FILENAME, &filename,
			COL_POINTER, &data, -1);
    p = (flash_file_info*)data;
    switch (p->filetype) {
    case FIROOT: //shouldn't happen
      strcpy(strfiletype, "ROOT");
      break;
    case FIDIR:
      strcpy(strfiletype, "DIRECTORY");
      break;
    case FIFILE:
      strcpy(strfiletype, "FILE");
      break;
    case FIPART:
      strcpy(strfiletype, "PARTITION");
      break;
    default:
      strcpy(strfiletype, "UNKNOWN");
      break;
    };
    
    snprintf(tempstring, STRINGSIZE - 1, "%s %d bytes   %s", filename, p->size, strfiletype);
    gtk_label_set_text(GTK_LABEL(information_label), tempstring);
  }
}


static gboolean do_download = FALSE;
static gboolean do_format = FALSE;
static gboolean do_help = FALSE;

static void process_args(int argc, char * argv[])
{
  int c;

  while (1) {
    int option_index = 0;
    static struct option long_options[] = {
      {"download", 0, 0, 'd'},
      {"format", 0, 0, 'f'},
      {"help", 0, 0, 'h'},
      {0, 0, 0, 0}
    };

    c = getopt_long (argc, argv, "dfh", long_options, &option_index);
    if (c == -1) break;
    
    switch (c) {
    case 'd':
      do_download = TRUE;
      break;

    case 'f':
      do_format = TRUE;
      break;
      
    case 'h':
      do_help = TRUE;
      break;
      
    case '?':
      break;
      
    default:
      printf ("?? getopt returned character code 0%o ??\n", 
	      c);
    }
  }

  if (optind < argc) {
    printf ("non-option ARGV-elements: ");
    while (optind < argc) {
      printf ("%s ", argv[optind++]);
      printf ("\n");
    }
  }
}
void EnableControls(gboolean value) {
  if (main_window) {
    unsigned int count;
    for (count = 0; count < NUM_OF_BUTTONS; ++count) {
      //      fprintf(stderr, "button: %08x\n", b_u.buttons[count]);
      gtk_widget_set_sensitive(b_u.buttons[count], value);

    }
  }
}


/*void EnableControls(gboolean value) {

  if (main_window) {
    gtk_widget_set_sensitive(button_open_camera, value);
    gtk_widget_set_sensitive(button_unlock, value);
    gtk_widget_set_sensitive(button_take_pic, value);
    gtk_widget_set_sensitive(button_close_camera, value);
    gtk_widget_set_sensitive(button_update_directory_listing, value);
    gtk_widget_set_sensitive(m_directory_tree, value);
    
  }
  }*/



int main (int argc, char *argv[])
{

  /* GtkWidget is the storage type for widgets */
  
  GtkWidget * vbox1, *hbox2, *hbox3, *hbox1, *hbox_progressbar, *hbox_tree, *hbox_label;
  GtkWidget* window;
  GtkWidget* s_w;
  GtkTreeViewColumn *col;
  GtkCellRenderer *renderer;
  GtkObject* hadjustment, *vadjustment;
  //GError* error = NULL;
  //camcorder_files_size = 0;
  g_thread_init(NULL);
  gdk_threads_init();
  
  root_directory = NULL;
  set_bitrate(0);
  /* This is called in all GTK applications. Arguments are parsed
   * from the command line and are returned to the application. */
  gtk_init (&argc, &argv);
  toggle_camera_lcd_screen_is_on = TRUE;
 
  // Handle the command line args
  process_args(argc,argv);
  
  if (do_help) {
    printf("flags:\n");
    printf("-d -- download all movies from the camcorder\n");
    printf("-f -- clear camera's movie partition (erase all movies)\n");
    printf("-h -- print this help info\n");
    printf("Flags may be combined to get a combined effect\n");
    exit(0);
  } else if (do_download || do_format) {
    int ret=0;
    
    if (open_camera(NULL,NULL,NULL)) {
      if (unlock_camera(NULL,NULL,NULL)) {

	//        if (do_download && !download_all_movies(NULL,NULL,NULL)) ret=1;
	//        if (do_format && !format_camcorder(NULL,NULL,NULL)) ret=1;
      }
      else ret=1;

      close_camera(NULL,NULL,NULL);
    }
    else ret=1;
    
    exit(ret);
  }
  
  //  stopwatch = 0;
    /* create a new window */
  main_window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  window = main_window;
  gtk_window_set_title (GTK_WINDOW (window), "PV2Tool for linux");
  
    /* When the window is given the "delete_event" signal (this is given
     * by the window manager, usually by the "close" option, or on the
     * titlebar), we ask it to call the delete_event () function
     * as defined above. The data passed to the callback
     * function is NULL and is ignored in the callback function. */
  gtk_signal_connect (GTK_OBJECT (window), "delete_event",GTK_SIGNAL_FUNC(delete_event), NULL);
    /* Here we connect the "destroy" event to a signal handler.  
     * This event occurs when we call gtk_widget_destroy() on the window,
     * or if we return FALSE in the "delete_event" callback. */
  gtk_signal_connect (GTK_OBJECT (window), "destroy", GTK_SIGNAL_FUNC (destroy), NULL);
  vbox1 = gtk_vbox_new (FALSE, 0);
  hbox2 = gtk_hbox_new (FALSE, 0);
  hbox3 = gtk_hbox_new (FALSE, 0);
  hbox1 = gtk_hbox_new (FALSE, 0);
  hbox_tree = gtk_hbox_new(FALSE,0);
  hbox_label = gtk_hbox_new(FALSE, 0);
  hbox_progressbar = gtk_hbox_new (FALSE, 0);
  
  

  gtk_box_pack_start (GTK_BOX (vbox1), hbox1, TRUE, TRUE, 0);
  gtk_box_pack_start (GTK_BOX (vbox1), hbox2, TRUE, TRUE, 0);
  gtk_box_pack_start (GTK_BOX (vbox1), hbox3, TRUE, TRUE, 0);
  gtk_box_pack_start (GTK_BOX (vbox1), hbox_progressbar, TRUE, TRUE, 0);
  gtk_box_pack_start (GTK_BOX (vbox1), hbox_tree, TRUE, TRUE, 0);
  gtk_box_pack_start (GTK_BOX (vbox1), hbox_label, TRUE, TRUE, 0);
  gtk_container_add (GTK_CONTAINER (window), vbox1);
  
  
  hadjustment = gtk_adjustment_new(0,-1,1,.1,.5,1);
  vadjustment = gtk_adjustment_new(0,-1,1,.1,.5,1);

  
  m_directory_tree = gtk_tree_view_new();
  //  m_directory_model = NULL;
  gtk_widget_set_size_request (m_directory_tree,
			       300,
			       300);

  s_w = GTK_WIDGET(gtk_scrolled_window_new(hadjustment, vadjustment));
  gtk_scrolled_window_set_policy (GTK_SCROLLED_WINDOW(s_w),
				  GTK_POLICY_AUTOMATIC,
				  GTK_POLICY_AUTOMATIC);
  //  gtk_container_set_height (GTK_TREE_VIEW (m_directory_tree), 300);
  //ICON COLUMN
  col = gtk_tree_view_column_new();
  gtk_tree_view_append_column(GTK_TREE_VIEW(m_directory_tree), col);
  renderer = gtk_cell_renderer_pixbuf_new();
  gtk_tree_view_column_pack_start(col, renderer, FALSE);
  gtk_tree_view_column_add_attribute(col, renderer, "pixbuf", COL_ICON);


  //COLUMN 1
  col = gtk_tree_view_column_new();
  gtk_tree_view_column_set_title(col, "filename");
  gtk_tree_view_append_column(GTK_TREE_VIEW(m_directory_tree), col);
  renderer = gtk_cell_renderer_text_new();
  gtk_tree_view_column_pack_start(col, renderer, TRUE);
  gtk_tree_view_column_add_attribute(col, renderer, "text", COL_FILENAME);

  //COLUMN 2
  col = gtk_tree_view_column_new();
  gtk_tree_view_column_set_title(col, "pointers");
  gtk_tree_view_append_column(GTK_TREE_VIEW(m_directory_tree), col);
  renderer = gtk_cell_renderer_text_new();
  gtk_tree_view_column_pack_start(col, renderer, TRUE);
  //  gtk_tree_view_column_add_attribute(col, renderer, "text", COL_POINTER);
  /*if (!g_thread_create(watch_progress_bar, NULL, FALSE, &error)) {
    Log(error->message);
    //go without if error
    }*/
  
  load_file_icons();
  information_label = gtk_label_new("");
  bitrate_label = gtk_label_new("");

  m_ctl_progress = gtk_progress_bar_new();

    /* Sets the border width of the window. */
    //gtk_container_set_border_width (GTK_CONTAINER (window), 10);
    /* Creates a new button with the label "Hello World". */

  create_and_display_button_short(open_camera, "Open Camcorder", hbox1);
  create_and_display_button_short(unlock_camera, "Unlock", hbox1);

			     GTK_SIGNAL_FUNC (gtk_widget_destroy),
			     GTK_OBJECT (window));
  
  gtk_box_pack_start (GTK_BOX (hbox_progressbar), m_ctl_progress, TRUE, TRUE, 0);
  gtk_box_pack_start (GTK_BOX (hbox_tree), s_w, TRUE, TRUE, 0);
  gtk_container_add (GTK_CONTAINER (s_w), m_directory_tree);

  //  gtk_box_pack_start (GTK_BOX (s_w), 
  //  gtk_box_pack_start (GTK_BOX (hbox_tree), button_update_directory_listing, TRUE, TRUE, 0);

  gtk_widget_show_all (window);
  gtk_timeout_add(REFRESH_DATA_MS,GTK_SIGNAL_FUNC(watch_progress_bar), NULL);
 

  gdk_threads_enter();
  gtk_main ();
  gdk_threads_leave();
  return 0;
}

//void Log(const char* st) {
//  fprintf(stderr, "%s\n", st);
//}

```

---

### Post by Chickencha on 2006-09-07
I copied and pasted the code you gave into a text editor so I could find line 380.  The code around that point looks like this:

```
GTK_SIGNAL_FUNC (gtk_widget_destroy),
GTK_OBJECT (window));
```

That's all one statement on its own.  It looks to me like these lines were originally arguments inside a function call of some kind, judging by the comma and the extra end parenthesis.

So probably you want to either A) Comment out these lines or B) Figure out what function call this is supposed to be.  You might take a look at the original, unmodified code if these lines weren't added by you.  Maybe you accidentally uncommented them or deleted part of the code.

---

