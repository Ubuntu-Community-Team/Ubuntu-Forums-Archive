---
title: "Gtk beginner"
date: 2010-08-10
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-08-10
I have problems with my code , if you can help me to solve it or even show me how to do the same thing in a totally different way 
I installed Glade interface designer but how can I use it with my code ?! 
```
#include <gtk/gtk.h>
#include <string.h>
GtkWidget *entry1;
GtkWidget *entry2;
GtkWidget *entry3;
/*to get the first integer from the first entry box*/
int get_first_number(GtkWidget *widget,gpointer data){
    gchar *p=gtk_entry_get_text(widget);
    int j=0,acc=0;
    while(p[j]!='\0'){
        acc=acc*10+(p[j]-'0');
        j++;
    }
    return acc;
}
/*to get the second integer from the second entry box*/
int get_second_number(GtkWidget *widget,gpointer data){
    gchar *p=gtk_entry_get_text(widget);
    int j=0,acc=0;
    while(p[j]!='\0'){
        acc=acc*10+(p[j]-'0');
        j++;
    }
    return acc;
}
/*the gcd function recursive way*/
int gcd(int a,int b)
{
    if(b==0)
    return a;
    else
    return gcd(b, a%b);
}
/*to reverse array of characters */
void reverse_char_array(char *array){
    int j=0,i,length=strlen(array);
    char array2[length];
    for(i=strlen(array)-1;i>=0;i--){
        array2[j]=array[i];
        j++;
    }
    i=0;
    for(i=0;i<length;i++)
        array[i]=array2[i];
}
/*to convert an integer >=10 to an array of characters*/
void result_to_array_of_char(int result,char array[]){
    int i;
    while(result != 0){
        array[i]=result%10+'0';
        i++;
        result=result/10;
    }
    reverse_char_array(array);
}
/*this is the function to activate when the calculate button is pressed */
void button_callback(GtkWidget *widget,gpointer data){
    int _1=get_first_number(entry1,NULL);
    int _2=get_second_number(entry2,NULL);
    int result=gcd(_1,_2);
    if(result<10){
        gchar c= result+'0';
        gtk_entry_set_text(entry3,&c);
        return;
    }
    char array[8]={'\0'};
    result_to_array_of_char(result,array);
    gtk_entry_set_text(entry3,array);

}
int main(int argc,char *argv[]){
    GtkWidget *window;
    GtkWidget *button;
    GtkWidget *table;
    GtkWidget *label1;
    GtkWidget *label2;
    GtkWidget *label3;
    gtk_init(&argc,&argv);
    window=gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title(GTK_WINDOW(window),"Calculating the GCD");
    g_signal_connect(G_OBJECT(window),"destroy",G_CALLBACK(gtk_main_quit),NULL);

/*    Using a table to draw with coordinates */
    table=gtk_table_new(4,2,FALSE);
    gtk_container_add(GTK_CONTAINER(window),table);

    label1=gtk_label_new("Enter the first integer");
    gtk_table_attach_defaults(GTK_TABLE(table),label1,0,1,0,1);
    gtk_widget_show(label1);
    entry1=gtk_entry_new();
    gtk_table_attach_defaults(GTK_TABLE(table),entry1,1,2,0,1);
    gtk_widget_show(entry1);

    label2=gtk_label_new("Enter the second integer");
    gtk_table_attach(GTK_TABLE(table),label2,0,1,1,2,GTK_EXPAND | GTK_FILL,GTK_EXPAND | GTK_FILL,15,0);
    gtk_widget_show(label2);
    entry2=gtk_entry_new();
    gtk_table_attach_defaults(GTK_TABLE(table),entry2,1,2,1,2);
    gtk_widget_show(entry2);

    button=gtk_button_new_with_label("Calculate");
    g_signal_connect(G_OBJECT(button),"clicked",G_CALLBACK(button_callback),NULL);
    gtk_table_attach_defaults(GTK_TABLE(table),button,0,2,2,3);
    gtk_widget_show(button);

    label3=gtk_label_new("The Result is");
    gtk_table_attach_defaults(GTK_TABLE(table),label3,0,1,3,4);
    gtk_widget_show(label3);
    entry3=gtk_entry_new();
    gtk_table_attach_defaults(GTK_TABLE(table),entry3,1,2,3,4);
    gtk_widget_show(entry3);

    gtk_widget_show(table);
    gtk_widget_show(window);
    gtk_main();
    return 0;
}
```
[IMG]http://lh5.ggpht.com/_tcUf5ZJRmuc/TGFAh7CQnDI/AAAAAAAAALA/CJumzJuCY70/Screenshot.png[/IMG]
[IMG]http://lh6.ggpht.com/_tcUf5ZJRmuc/TGFAh0GhaaI/AAAAAAAAALE/faE9allpCTc/Screenshot-1.png[/IMG]
*[SIZE=4][COLOR=Red]the error appears in the first picture [/COLOR][/SIZE]*

---

### Post by dwhitney67 on 2010-08-10
Rewrite the following code:
```

void result_to_array_of_char(int result,char array[]){
    int i;
    while(result != 0){
        array[i]=result%10+'0';
        i++;
        result=result/10;
    }
    reverse_char_array(array);
}

```
Try something straightforward, like:
```

void toString(int value, char* buffer) {
   sprintf(buffer, "%d", value);
}

```
Of course, don't shoot yourself in the foot by providing a buffer that is too small to hold the value.

---

### Post by nvteighen on 2010-08-10
Hey, congratulations! You're only of the very few beginners that write nicely modularized GUI code! There might some places where some rework could be done, but you got the general idea and you're on the right track. For example, you better declare the entry1 and entry widgets in your main procedure and pass them where needed... That way you ensure explicit modularization.

About Glade. Read the docs. IIRC, you have to use a library and "activate" the interface (saved in a file) by the functions it provides. Never used it myself, so I'm not much of help, but that's the idea.

---

