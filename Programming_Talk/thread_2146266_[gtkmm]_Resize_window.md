---
title: "[gtkmm] Resize window"
date: 2013-05-17
forum: Programming Talk
---

### Post by limapapy on 2013-05-17
Hi people i'm new in gtkmm and my English is not so good.
I'm doing a picture organizer and i'm in the beginning of the project.
I have a top bar (frame) where i will put some functionality buttons, the left 
side bar(frame) where i will have picture tags and the main frame in the right 
that i will display the set of pictures, and individual picture too.
in the rigth frame (main frame) i show the pictures inside off a grid.
Until there, good. 
When a maximize the window the grid is redesigned to fit the pictures in the
screen(thats ok). But when i restore the window to the previous size i'm having problems 
in resizing the window.
I'm using two signals - signal_check_resize() and signal_window_state_event.
On the first occur every time you re-size the window, and the second occur when the 
window is maximized restored or minimized.

Any ideia on how to do it.
This is a picture of the window.
[IMG]https://dl.dropboxusercontent.com/s/21t81sjhrqx3efs/tagx.png?token_hash=AAFbh-mgDt9Te8uPB_MuzaJ1GIR8gCmmHuO_U2zxstW7zA&dl=1[/IMG]

---

### Post by r-senior on 2013-05-18
Which part do you have a problem with?

1. Catching the window state event?
2. Refreshing the layout of the grid when the window is restored?

I have some code that handles the window state event. It's C/GTK rather than gtkmm, but the idea is the same:

```
    GdkWindow *window = gtk_widget_get_window(w);
    GdkWindowState state = gdk_window_get_state(window);
    gboolean maximized = state & GDK_WINDOW_STATE_MAXIMIZED;

    if (maximized)
        // do something

```

You should be able to extend that for the other states.

---

### Post by limapapy on 2013-05-18
> **r-senior said:**
> Which part do you have a problem with?

1. Catching the window state event?
2. Refreshing the layout of the grid when the window is restored?

I have some code that handles the window state event. It's C/GTK rather than gtkmm, but the idea is the same:

```
    GdkWindow *window = gtk_widget_get_window(w);
    GdkWindowState state = gdk_window_get_state(window);
    gboolean maximized = state & GDK_WINDOW_STATE_MAXIMIZED;

    if (maximized)
        // do something

```

You should be able to extend that for the other states.


Thanks for reply
In my code a catch the maximized a minimized state. 
The problem is with the signal_check_resize.
here is my handler of signal_window_state_event
```

  bool GuiTag::window_state_change(GdkEventWindowState* event){  cout<<"resize has been called "<<signal<<" times"<<endl;
  signal=0;


  //when window is restored or maximized                                                   
  if((event->changed_mask & GDK_WINDOW_STATE_MAXIMIZED) > 0){
    if(maximized){
      cout<<"window has been maximized. prev: "<<this->get_width()<<endl;
       //save the restore width
      restore_window_width = this->get_width();
    }else{
      cout<<"window has been restored. prev: "<<this->get_width()<<endl;
      state_changed = true;
    }
    maximized = !maximized;
  }
  return true;
}



```

and the code for resize_chek that handle every window 
resize, even the maximize and restore.

```

void GuiTag::on_window_resize(){
  if(window_width != this->get_width()){
    cout<<"window has been resized "<<this->get_width()<<endl;


    if(state_changed){
      cout<<"restoring window size"<<endl;
      window_width = restore_window_width;
    }else{
      //window resized manualy                                                             
      window_width = this->get_width();
    }
    float fw,ww,bw,lv,mw,fcn;
    int cn;
    bw = (float) (BORDER_WIDTH);
    //side bar width                                                                       
    lv = (float) (TAG_LIST_WIDTH);
    ww = (float) window_width;
    //grid miniature width                                                                 
    mw = (float) (MINIATURE_WIDTH);
    //width to be resized                                                                  
    ww = (float) window_width;
    fw = ww - 6 * bw -lv;
    fcn = (fw - 3 * bw) / (mw + 2 * bw);
    cn = ( int ) fcn;
    ncols = cn;
    //current is the object with the pictures                                              
    if(current != NULL){
      cout<<"displaying in the new grid"<<endl;
      display_images(current->getImages());
      Gtk::Allocation allocation;
      allocation = this->get_allocation();
      allocation.set_width(window_width);
      cout<<"allocating window: "<<window_width<<endl;
      this->size_allocate(allocation);
    }
    state_changed = false;
  }else{
    cout<<"false enter"<<endl;
  }
}



```

---

### Post by limapapy on 2013-05-20
Its solved.
I use 
```

this->resize(restore_window_width,restore_window_height);

```

---

