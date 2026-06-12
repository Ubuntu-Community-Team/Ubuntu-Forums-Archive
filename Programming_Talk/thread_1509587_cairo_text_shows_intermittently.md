---
title: "cairo text shows intermittently"
date: 2010-06-14
forum: Programming Talk
---

### Post by tbastian on 2010-06-14
I'm attempting to draw mouse coordinates at the bottom of a canvas I'm using. I've got the code inside my 'mouse motion event' callback. For some reason it will show the first time I click and drag the mouse, but then disappear and never come back after that. The event IS being called, the xy coordinates are right (I put in a printf call at one point). Maybe I'm doing something else wrong??

[PHP]	if ( plot -> mouse_coord ) {
		x = 0.85 * width;
		y = 0.98 * height;

		cairo_set_source_rgb ( canvas -> cr, 1.0, 1.0, 1.0 ); //white
		cairo_rectangle ( canvas -> cr, x, y, extents . width, extents . height );
		cairo_fill ( canvas -> cr );//erase previous text
		cairo_stroke ( canvas -> cr );

		cairo_select_font_face ( canvas -> cr , "serif" , CAIRO_FONT_SLANT_NORMAL , CAIRO_FONT_WEIGHT_NORMAL );
		cairo_set_font_size ( canvas -> cr, 12 );
		cairo_set_source_rgb ( canvas -> cr, .1, .1, .1 );//grayish

		cairo_move_to ( canvas -> cr , x , y );
		cairo_show_text ( canvas -> cr, "this is text" );
		cairo_text_extents ( canvas -> cr, "this is text", &extents );
	}[/PHP]

---

