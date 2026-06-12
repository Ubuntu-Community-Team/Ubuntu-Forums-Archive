---
title: "gtkextra - gtkplot"
date: 2010-04-03
forum: Programming Talk
---

### Post by tbastian on 2010-04-03
I'm writing an application using gtkplot, and when I try build it, the compiler complains on this line of code:

```
gtk_plot_data_set_line_attributes ( data [ num_series ],
				GTK_PLOT_LINE_SOLID,
				0, 0, 1., &color );
```

This is the compiler output:

```
src/PlotPanel.cc: In member function ‘void PlotPanel::add_series(Series)’:
src/PlotPanel.cc:117: error: invalid conversion from ‘int’ to ‘GdkCapStyle’
src/PlotPanel.cc:117: error:   initializing argument 3 of ‘void gtk_plot_data_set_line_attributes(GtkPlotData*, GtkPlotLineStyle, GdkCapStyle, GdkJoinStyle, gfloat, const GdkColor*)’
src/PlotPanel.cc:117: error: invalid conversion from ‘int’ to ‘GdkJoinStyle’
src/PlotPanel.cc:117: error:   initializing argument 4 of ‘void gtk_plot_data_set_line_attributes(GtkPlotData*, GtkPlotLineStyle, GdkCapStyle, GdkJoinStyle, gfloat, const GdkColor*)’

```

This is bothering me because that line is directly copied out of one of the examples included in the gtkextra package!

Does anyone have any ideas??

---

### Post by tbastian on 2010-04-03
I just realized that the given API doesn't actually match reality. I looked at the API and it says the function stub is:

```
void gtk_plot_data_set_line_attributes (GtkPlotData *data,
                                              GtkPlotLineStyle style,
                                              gfloat width,
                                              const GdkColor *color); 
```

whereas the .h file says it is:

```
void		gtk_plot_data_set_line_attributes 	(GtkPlotData *data,
						 	 GtkPlotLineStyle style,
						 	 GdkCapStyle cap_style,
						 	 GdkJoinStyle join_style,
						 	 gfloat width,
						 	 const GdkColor *color);
```

Is this something I should make the developers aware of?

---

### Post by tbastian on 2010-04-26
The reason for this was because I was using g++, and the original example compiled with gcc. Apparently they do something different when it comes to casting enums to other data types.

---

