---
title: "Gtk print operation example problem"
date: 2010-04-08
forum: Programming Talk
---

### Post by bcz on 2010-04-08
Hi all

I  am playing with draw_page callback code on the net, and get
"HEADER_HEIGHT" undeclared.  As this is uppercase identifier, I assume it is in part of Pango/Cairo/GtkPrintOperation.

Any hints on my error appreciated

static void drawPage(GtkPrintOperation *oper,GtkPrintContext *cntxt,gint pgNr,gpointer usrDta){
        cairo_t *cr;
        PangoLayout *layout;
        gdouble wdth,txtHght;
        gint layoutHght;
        PangoFontDescription *desc;

        cr=gtk_print_context_get_cairo_context(cntxt);
        wdth=gtk_print_context_get_width(cntxt);
        cairo_rectangle(cr,0,0,wdth,HEADER_HEIGHT);
        cairo_set_source_rgb(cr,0.8,0.8,0.8);
        cairo_fill(cr);

        layout=gtk_print_context_create_pango_layout(cntxt);
        desc=pango_font_description_from_string("sans 14");
        pango_layout_set_font_description(layout,desc);
        pango_font_description_free(desc);

        pango_layout_set_text(layout,"text TEXT text",-1);
        pango_layout_set_width(layout,wdth*PANGO_SCALE);
        pango_layout_set_alignment(layout,PANGO_ALIGN_CENTER);
        pango_layout_get_size(layout,NULL,&layoutHght);
        txtHght=(gdouble)layoutHght/PANGO_SCALE;

        cairo_move_to(cr,wdth/2,(HEADER_HEIGHT-txtHght)/2);
        pango_cairo_show_layout(cr,layout);
        g_object_unref(layout);
        }

---

### Post by bcz on 2010-04-08
I notice a smiley in the original post.  Dont know how it got there, but it is not in actual code.  (I retyped the end of the strange line and recompiled.  HEADER_HEIGHT problem still ther)

Rgds Bill C

---

### Post by bcz on 2010-04-08
Have inserted "#define  HEADER_HEIGHT 25" in code to progress my investigation

Will update thread if I learn more about above

Rgds Bill C

---

### Post by bcz on 2010-04-09
I find HEADER_HEIGHT and HEADER_GAP are application level #defines set in one print example code as 20.0 and 8.5 respectively

Google books... Foundations of GTK+ Development Andrew Krause

Might get the book as my GTK hardcopy reference is ~10 years old

Rgds Bill

---

