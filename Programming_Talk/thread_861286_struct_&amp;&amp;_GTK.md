---
title: "struct &amp;&amp; GTK"
date: 2008-07-16
forum: Programming Talk
---

### Post by hamid206 on 2008-07-16
I have 2 struct and 2 window .

When I clicked on button in window one , this send d_wid to window 2 and d_wid (SANDOGH) copy in s_wid (TSANDOGH) ,in create_t_sandogh func

But in delete_event in window2 (create_t_sandogh) when I free TSANDOGH (s_wid) , SANDOGH (d_wid) too free and become invalid

How to copy SANDOGH (d_wid) on TSANDOGH (s_wid) when I free TSANDOGH , SANDOGH not free ? 
```

typedef struct
{
GtkListStore *store ;
GtkWidget *label ;
}SANDOGH ;

/************************************************/
typedef struct
{
GtkWidget *wid[3];
gint64 praice ;
int data ;
char *date ;
SANDOGH *sandogh ;
}TSANDOGH ;

/*************************************************/

gint form_delete( GtkWidget *widget, GdkEvent *event,TSANDOGH *s_wid )
{
    g_free(s_wid->date);
    g_slice_free(TSANDOGH,s_wid);
  return false;
}

/*****************************************************/

void create_t_sandogh(GtkWidget *wid,SANDOGH *sand)
{

TSANDOGH *s_wid ;
s_wid=g_slice_new(TSANDOGH);

s_wid->wid[0]=gtk_window_new(GTK_WINDOW_TOPLEVEL);
s_wid->wid[1]=....
......
       
s_wid->sandogh=sand ;

.....
       
g_signal_connect(s_wid->wid[0], "delete_event",G_CALLBACK (form_delete),(gpointer)s_wid);

gtk_widget_show_all(s_wid->wid[0]);
}



void sandogh_func(GtkWidget *wid,gpointer data)
{
SANDOGH *d_wid ;
d_wid=g_slice_new(SANDOGH);

GtkWidget *window,*treeview,*button;

window=gtk_window_new(GTK_WINDOW_TOPLEVEL);
treeview=gtk_tree_view_new();
d_wid->label=gtk_label_new("125");
button=gtk_button_new_with_label("Send Info");

GtkCellRenderer *renderer;
GtkTreeViewColumn *column;
renderer = gtk_cell_renderer_text_new ();
g_object_set (G_OBJECT (renderer),"xalign",0.5, NULL);
column = gtk_tree_view_column_new_with_attributes("Type", renderer ,"text",0, NULL);
.....

d_wid->store=gtk_list_store_new(3,G_TYPE_STRING,G_TYPE_STRING,G_TYPE_STRING);
gtk_tree_view_set_model (GTK_TREE_VIEW (treeview), GTK_TREE_MODEL (d_wid->store));

...
 g_signal_connect(button,"clicked",G_CALLBACK (create_t_sandogh),(gpointer)d_wid);
......
       
gtk_widget_show_all(window);

} 

```

---

