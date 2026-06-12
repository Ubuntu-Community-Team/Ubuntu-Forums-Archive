---
title: "Is there a kind of conflict between gtkmm and opencv?"
date: 2013-04-26
forum: Programming Talk
---

### Post by Vincent66 on 2013-04-26
Hi,

  

  I would use the OpenCV libraries into a program using the Gtkmm graphic interface but when I try to open an image with cv::imread, there is an error message during the execution : gtk-error ** Using gtk+ 2.x and gtk+ 3 in the same process is not supported.

  

  Here is a very simple sample code :

#include <gtkmm/main.h>
#include <gtkmm/window.h>
#include <gtkmm/image.h>

#include "opencv2/highgui/highgui.hpp"

int main(int argc, char* argv[]) {

  Gtk::Main app(argc, argv);
  Gtk::Image ImgGtk;
  Gtk::Window Win0;
  cv::Mat ImgOcv;

  Win0.set_border_width(5);
  Win0.set_default_size(250, 100);

  ImgOcv= cv::imread("icone.png", -1);
  ImgGtk.set("icone.png");
  Win0.add(ImgGtk);

  Win0.show_all();
  Gtk::Main::run(Win0);

  return 0;
}


  The idea is to replace   ImgGtk.set("icone.png"); by a create_from_data and a gtk_img.set(pixbuf);
The code above compile perfectly fine, but produce the above mentionned error during the exceution.  Just remove the line 17,   ImgOcv= cv::imread("icone.png", -1); and the error disapear, the image is displayed by ImgGtk.set("icone.png");.

 
Does anyone have heard about this kind of conflict?
Does anyone have an idea to where I could post this question?

  

  I am using gtkmm 3.0 and have upgraded opencv to 2.4.5 but this did not solve the problem.
  The operating system is Ubuntu 12.04.
  

  Thank you in advance.

---

