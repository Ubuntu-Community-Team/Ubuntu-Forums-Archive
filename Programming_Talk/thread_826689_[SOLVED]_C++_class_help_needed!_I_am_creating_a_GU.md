---
title: "[SOLVED] C++ class help needed! I am creating a GUI library..."
date: 2008-06-12
forum: Programming Talk
---

### Post by irrdev on 2008-06-12
**This thread is solved!** :) The workaround was to use a combination of virtual functions in the "Widget" class and static casting to make Widget-derived classes work with a <Widget*> vector. For those interested in reading about this, check out [http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.6]("http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.6").

I am nearly ripping my hair in frustration over this problem. There is definitely a solution which I am unable to see. Sorry for the lengthy post, but you can skip over reading most of the code...

I am creating a custom GUI library which uses widgets in an object-oriented way. Every widget is based from a generic widget class similar to the following:
[PHP]
    class Widget
    {
    public:
        Widget();
        virtual ~Widget();
        void draw();
        // more functions here...
    };
[/PHP]
Each widget, such as a button, then inherits the widget class:
[PHP]
    class Button: public Widget
    {
    public:
        Button();
        virtual ~Button();
        // We override the draw() function to draw this specific widget
        void draw();
        // more functions here...
    };
[/PHP]
All the widgets are to be drawn in a window class like the following:
[PHP]  class Window
    {
    public:
        Frame(string title)
        virtual ~Frame();

        // Create a vector of Widgets
        std::vector <Widget> Widgets;

        template <class WidgetType>
        void add(WidgetType *w)
        {
           /*
              HERE'S THE PROBLEM! I need to take the custom widget(button,checkbox, etc.) and 
              store it as a generic widget in the "Widgets" vector. 
This is so that I can iterate through the widgets later to draw them in the window, USING THE DERIVED DRAW FUNCTION found in the custom widget class, such as a button! 
*/
        }
     };[/PHP]
The code to use the library would like this:
[PHP]
Window *window = new Window("hi there");
Button* button = new Button();
// This is what I want to be able to do
window->add(button);
[/PHP]
Look at the code for the "Window" class to identify my problem. I need to convert all of the incoming derived widgets to plain widgets so that I can store them in a vector. Then, I can later iterate through the Widgets and call the draw() function. 

The solution to this problem is probably very simple, but I haven't done this type of thing before. Explicitly casting the classes to type "Widget" doesn't do the trick, as it doesn't use the derived draw() function from the "Button" class. 

What's the best solution to this problem? Any help would be great!

---

### Post by kknd on 2008-06-12
Well, you shouldn't have to cast anything.

Just make the draw method virtual, overload it in the derived classes and call it. This is called polymorphism.

---

