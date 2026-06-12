---
title: "gtk issue with multiple call in a function"
date: 2011-01-08
forum: Programming Talk
---

### Post by eternal_winds on 2011-01-08
Hi,

first sorry for my poor english,

I'm starting in Gtk usage and i met a problem,
i call a display function inwich i call many time a G_function to place an image in a fixed, each litlle shifted.
my code is : 


```
GtkWidget affichagetableau (char** t,int taillet,GtkWidget* fixed)    // fonction d'affichage du tableau
{
    GtkWidget *image;

    image = gtk_image_new_from_file("trou.png");
    int i,j,k;
    for(i=0; i<taillet; i++)        //balayage des lignes
    {
           for(j=0; j<taillet; j++)    //balayage des collones
        {
              gtk_fixed_put(GTK_FIXED(fixed), image , i*97 , j*98);
        }
    }
return *fixed;
}
```there is my function code,

as for my main i've writtten:

```
int main(int argc,char* argv[])
{
int choix = 0;
int jouer = 1;
int taillet = 3;

//la fenetre  
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_window_set_title(GTK_WINDOW(window), "GtkButton");
  gtk_window_set_default_size(GTK_WINDOW(window), 800, 600);
  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);

//le fixed
  fixed = gtk_fixed_new();
  gtk_container_add(GTK_CONTAINER(window), fixed); 

button = gtk_button_new_with_label("continuer");
  gtk_fixed_put(GTK_FIXED(fixed), button, 725, 0); //position dans la fenetre
  gtk_widget_set_size_request(button, 75, 40);     //taille du bouton

g_signal_connect(button, "clicked", G_CALLBACK(afficher), (gpointer) &choix);


while (jouer==1)
{

 

      gtk_widget_show_all(window);
      gtk_main();

      if (choix == 1)
      {
          affichagetableau(t,taillet,fixed);
      }

  }

}
```the afficher function change variable choix to 1;
the .png is in the right folder,
it build well and all,but when i launch the program,when it reach the function affichertableau and try to put the *.png in the fixed the seems to be placed but as for the seconde (i=0,j=1) and the rest it gives me this error in the console :
(monprojet:12176): Gtk-WARNING **: Can't set a parent on widget which has a parent


to finish when i look the main window created, only the last .png appears...
Does someone can explain me my mistakes?

ho, and i'd like to know if it's preferable to set my affichertableau type as GtkWidget* or to GtkWidget  in order to have my fixed well modified in the main?

thanks

---

### Post by gmargo on 2011-01-08
I would guess that you can't reuse the GtkWidget generated from the "gtk_image_new_from_file()".  The first time through the widget is placed in the fixed container, and so its parent is now the fixed container.  Then you put the same widget in the fixed container again - but the widget already has a parent assigned so you get the warning.

---

### Post by eternal_winds on 2011-01-08
and for the function type is it ok?

so i just have to reload the image? thanks, i'll try it.

---

### Post by worksofcraft on 2011-01-08
> **eternal_winds said:**
> and for the function type is it ok?

so i just have to reload the image? thanks, i'll try it.

Yes I use the following function call to change an image:
```

	gtk_image_set_from_file((GtkImage *) pW, pFileName);

```
pW is a pointer to my GtkImage widget and pFileName points to the name of the image file that I want to display and there is no need to erase the old image.

---

### Post by eternal_winds on 2011-01-08
when i used yout function i get a lot of error message :

(myproject:32620): Gtk-CRITICAL **: gtk_fixed_put: assertion `GTK_IS_WIDGET (widget)' failed
i = 2 , j = 1

(myproject:32620): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

(myproject:32620): Gtk-CRITICAL **: gtk_image_set_from_file: assertion `GTK_IS_IMAGE (image)' failed

but when i rewrite :
image = gtk_image_new_from_file("trou.png");
at each time i call my image, it works :confused:

anyway, this way, it works so problem solved :)


but that's not all.
after this i want to put toggle_button under the images, the problem is that these are png's with a big hole in the center that let appears what is under, and in that way we can see the button under;
i thought to the function gtk_toggle_button_set_mode and used it that way , without success :

```

buttonc = gtk_toggle_button_new_with_label("bouton collone");

gtk_widget_set_size_request(buttonc, 97, taillet*98); 
       
gtk_toggle_button_set_mode (GTK_TOGGLE_BUTTON (buttonc), TRUE);

gtk_fixed_put(GTK_FIXED(fixed),buttonc , 100 + i*97, 50);

```

buttonc is well declared as gtk_toggle_button;
i can't get it invisible ... :/

also, i want to repeat this button  as many time as i have columns in a row,is it the right way to set button with each a different id?

[IMG]file:///home/eternal/Bureau/Screenshot.png[/IMG]

---

### Post by eternal_winds on 2011-01-08
sry, i don't know how to host my preview...

---

### Post by worksofcraft on 2011-01-08
> **eternal_winds said:**
> sry, i don't know how to host my preview...

Click on Manage Attachments and then attach your image file. Once it is uploaded it has URL that you can use with IMG tags like so:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180531&stc=1&d=1294542148[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180532&stc=1&d=1294542148[/IMG]

These I use in my coffee vending machine simulator...
[php]
void vending_machine::start_making_coffee() {
	status("Your wish is my command, oh great one!");
	iFill = 0; // empty
	widget("image1").set("emptycup.JPG");
	start(&vending_machine::making_coffee);
}
// ... etcetera
[/php]

---

### Post by eternal_winds on 2011-01-09
i don't see the relation with my problem :/
the fact is that i have button under a png that i want to be invisible ... and i can't.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180556&stc=1&d=1294573753[/IMG]

there you see the ugly button that may vanish.

---

### Post by eternal_winds on 2011-01-09
i solved my problem by reinserting my background image over the button ...

---

### Post by worksofcraft on 2011-01-09
> **eternal_winds said:**
> i solved my problem by reinserting my background image over the button ...

Très bien :)

btw I know my images were not related to your problem, I was posting them so you could see how to post your preview... I was sort of also mentioning that I just set one image at a time in my widget, so what I really meant was that I could't help with the *actual* problem.

If you do find you want to show the real background through holes the [x rendering extensions]("http://en.wikipedia.org/wiki/XRender") will support alpha blending so presumably you can just set total transparency on the holes?

---

