---
title: "gtkmm glib"
date: 2007-11-22
forum: Programming Talk
---

### Post by Moezzie on 2007-11-22
Hey guys!

Since there is no Gtkmm forum(at least i cant find one) i hope you ubuntuguru could maybe help me out a bit.

Im farely new to gtkmm. Started about a week ago, everythings gone fine untill now. 
Im making a small timer app with just a start button so far. Though I cant get the label to display the elapsed time.

Here is the part of my code that hadles that stuff.
[PHP]
//using namespace Glib;
//timer is from glib.h


//execute when button is clicked
void MyWindow::on_button_clicked()
{
     //    This works
    //m_label1.set_markup("Something random");
    //m_label1.set_use_markup(true);
 
    //In here it does not work
    MyWindow::setTime();
}

//function that gets the elapsed time
void MyWindow::setTime()
{
   Timer timer;
   std::string string;
   double elapsed;
while(true)
    {
        if(timer.elapsed())
	{
	    elapsed = timer.elapsed();
	    string = stringify(elapsed);

	    std::cout << string << "\n";
	    MyWindow::setLabel(string);
      
    	}
//wait one second before next loop
    sleep(1);
    }
}

//change the labels text
void MyWindow::setLabel(std::string s)
{
      m_label1.set_markup(s);
      m_label1.set_use_markup(true);
}

[/PHP]

Puting a cout to check the string before passing it on to setLabel works fine. So i dont see why it the label wont display it.

I get no syntax errors or any kind of warning, it just does not work. The label does'nt change.
Any ideas?

---

