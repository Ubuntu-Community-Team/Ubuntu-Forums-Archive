---
title: "c++ class data member pointer questions"
date: 2009-08-03
forum: Programming Talk
---

### Post by blake82 on 2009-08-03
Hi Folks,

I'm having a problem with a class I'm writing.
I'm trying to pass a pointer of a public data member to a class instance within the class

```

class foo{
private:
  bar barObj;
public:
  float value;
  void init(){
    barObj.setPointer(&value);
  }
};

```

So if "bar" is a class, and I try to pass the address of value to it, it just passes NULL, and I get a segmentation fault when "bar" tries to dereference it.

Any ideas on why this isn't working???

Thanks,

Blake

---

### Post by Mirge on 2009-08-03
Actual source would be helpful :)

---

### Post by blake82 on 2009-08-03
ok here's the member in question:

```
class qtDial{
private:
    //ui objects
    QDial dial;
    QLabel nameLabel;
    QLabel valueLabel;
    string name;
    string suffix;
    bool suffixFlag;
    stringstream txtBuffer;
    QWidget* parent;
    //ui settings
    int size;
    int posX;
    int posY;
    int uiMin;
    int uiMax;
    int uiStart;
    //value scale settings
    int lastVal;
    float valMin;
    float valMax;
    float tempVal;
    float value;
    //pointer to destination
    float* dest;
public:
    
    void setDsplyValues(int dSize, int dPosX, int dPosY){
        size = dSize;
        posX = dPosX;
        posY = dPosY;
    }
    void setUiValues(int min, int max, int start){
        uiMin = min;
        uiMax = max;
        uiStart = start;
    }
    void setNameAndParent(string nme, string sfx, QWidget* par){
        name = nme;
        suffix = sfx;
        parent = par;
        //set suffix flag
        suffixFlag = (suffix.length() > 0);
    }
    void setScaleValues(float min, float max){
        valMin = min;
        valMax = max;
    }
    void setPointer(float* dst){
        dest = dst;
    }
    void updateValue(){
        if(lastVal != dial.value()){
            tempVal = ((float)(dial.value() - uiMin)) / ((float)(uiMax - uiMin));
            //transform from (x..y) -> (0..1)
            value = (tempVal * (valMax - valMin)) + valMin;
            txtBuffer.str("");
            txtBuffer << value;
            if(suffixFlag){
                txtBuffer << " ";
                txtBuffer << suffix;
            }
            valueLabel.setText(txtBuffer.str().c_str());
            cout << name << " changed to " << txtBuffer.str() << endl;
            txtBuffer.str("");
            lastVal = dial.value();
        }
        *dest = value;
    }

    void init(){
        string work;

        //init dial
        work.assign(name);
        work.append("_DIAL");
        dial.setParent(parent);
        dial.setGeometry(posX, (posY), size, size);
        dial.setObjectName(work.c_str());
        dial.setNotchTarget(4.0);
        dial.setNotchesVisible(true);
        dial.setMinimum(uiMin);
        dial.setMaximum(uiMax);
        dial.setValue(uiStart);
        dial.show();

        //init name label
        work.assign(name);
        work.append("_LABEL");
        nameLabel.setParent(parent);
        nameLabel.setGeometry(0, 0, (size), 15);
        nameLabel.setAlignment(Qt::AlignCenter);
        nameLabel.setObjectName(work.c_str());
        nameLabel.setText(name.c_str());
        nameLabel.move(posX, (posY - 15));
        nameLabel.show();

        //init value label
        work.assign(name);
        work.append("_VALUE");
        valueLabel.setParent(parent);
        valueLabel.setGeometry(0, 0, (size), 15);
        valueLabel.setAlignment(Qt::AlignCenter);
        valueLabel.setObjectName(work.c_str());
        valueLabel.move(posX, (posY+size));
        valueLabel.show();
        updateValue();
    }
};
```

and here's it's owner that tries to pass a pointer to it

```
class analogOscBankGUI{
private:
    //UI elements
    QWidget* parent;
    qtGroupBox oscBox;
    qtDial semi;
    qtDial detune;
    qtRadioButton shape;
    //ui settings
    string name;
    int posX;
    int posY;
    
public:
    //values
    float semiVal;
    float detuneVal;
    int shapeVal;

    void setPos(int x, int y){
        posX = x;
        posY = y;
    }
    void setNameAndParent(string nme, QWidget* par){
        name = nme;
        parent = par;
    }
    void init(){
        //init values
        semiVal = 0;
        detuneVal = 0;
        shapeVal = 0;
        
        oscBox.setParent(parent);
        oscBox.setName(name);
        oscBox.setPos(posX,posY);
        oscBox.setSize(200,200);
        oscBox.init();

        semi.setDsplyValues(50,5,30);
        semi.setUiValues(-36,36,0);
        semi.setNameAndParent("semi", "", oscBox.pointer);
        semi.setPointer(&semiVal);
        semi.setScaleValues(-36,36);
        semi.init();

        detune.setDsplyValues(50,5,120);
        detune.setUiValues(-100,100,0);
        detune.setNameAndParent("detune", "", oscBox.pointer);
        detune.setPointer(&detuneVal);
        detune.setScaleValues(-1,1);
        detune.init();

        shape.setParent(oscBox.pointer);
        shape.setNumElements(4);
        shape.setBoxName("Wave");
        shape.setPos(70, 15);
        shape.setSize(55,80);
        shape.setElement(0,"sin");
        shape.setElement(1,"tri");
        shape.setElement(2,"saw");
        shape.setElement(3,"sqr");
        shape.setPointer(&shapeVal);
        shape.init();
    }
    void updateValues(){
        semi.updateValue();
        detune.updateValue();
        shape.updateValue();
    }
};
```

when I try to pass a pointer to the member it just passes null

---

### Post by dwhitney67 on 2009-08-03
I did not have time to examine your code closely, and I am unable to build it in a speedy manner since it *appears* to be using Qt.

As Mirge had requested, always post **complete** code... not just snippets, because it makes it difficult for others to determine your runtime issues.

Here's a silly piece of code that mimics what you are attempting, and it works fine.
```

#include <cassert>

class Shape
{
public:
   Shape() {}
   void setPointer(int* ptr) { value = ptr; }
   int* getPointer() const   { return value; }
private:
   int* value;
};

class Foo
{
public:
   Foo() {}
   void init()
   {
      shape.setPointer(&value);
      assert(&value == shape.getPointer());
   }
private:
   Shape shape;
   int   value;
};

int main()
{
   Foo f;
   f.init();
}

```

---

### Post by Mirge on 2009-08-03
EDIT: see dwhitney's post :)

---

### Post by blake82 on 2009-08-03
EDIT: ok it is in fact passing addresses, but it still seg faults when it attempts to dereference them at runtime

---

### Post by dwhitney67 on 2009-08-03
blake82, you have got to post your code... in it's entirety.

As much as I wish to the contrary, I am not psychic.  I doubt no one else that participates on the forum is either.

I have no idea what is a qtRadioButton, much less what it's init() method is doing.

At first glance at your code, I expect to be hit with a meatball.  You definitely have already served up the spaghetti.

Now, could you please add some class constructors, dispense with the init() methods, and refine your code a bit.  It also would be helpful to see some comments, and to have an idea of what you are trying to accomplish.

Also, have you used "gdb" yet to debug your code?

---

### Post by blake82 on 2009-08-03
Sorry dwhitney67, my code is normally thoroughly commented :)

I'll comment it out and repost with better explanations of what's going on.

---

### Post by dwhitney67 on 2009-08-03
> **blake82 said:**
> Sorry dwhitney67, my code is normally thoroughly commented :)

I'll comment it out and repost with better explanations of what's going on.

At a minimum, please examine whether you indeed wanted to init() the shape object:
```

        ...
        shape.setElement(3,"sqr");
        shape.setPointer(&shapeVal);
        shape.init();

```
Perhaps you are zero-ing out the address that you store with the setPointer().

---

### Post by Mirge on 2009-08-03
> **dwhitney67 said:**
> 
at first glance at your code, i expect to be hit with a meatball.  You definitely have already served up the spaghetti.


lmao:p

---

### Post by Mirge on 2009-08-03
Yeah, that was signature worthy.

EDIT: To be clear, I'm not laughing at your code or you, blake... I just found the remark hilarious. :)

---

### Post by blake82 on 2009-08-03
Ok, so thanks for telling me to clean up my code. Something I did during that process solved my problem.

I managed to remove the init() functions

So, in case you're curious (or can offer any additional constructive criticism or tips). I'm building a platform for creating synthesizers and other musical instruments that run on JACK / QT, which I may eventually port over to vst / au.

What I'm working on right now is a set of classes that allow me to quickly create a UI without too much tinkering or QT pain so I can focus on the experimental DSP stuff I want to do. Basically the idea is to make ui module classes that the polyphonic voice system can be cleanly paired to without a lot of messy code, customized for each parameter. My goal is to have as much contained in the primitives as possible, so my UI modules can be assembled quickly.

As far as the UI is concerned, here is the code for the primitives and a simple oscillator module (you saw both earlier, just cleaned up). This is pretty much it, except for the QT application and main window declarations, and a function call in the JACK process function that asks the ui to update it with new values.

The primitives:

```
/* 
 * File:   uiElements.h
 * Author: blake
 *
 * Created on August 2, 2009, 2:00 PM
 */

#ifndef _UIELEMENTS_H
#define	_UIELEMENTS_H

#include <string>
#include <sstream>
using namespace std;

#include <QDial>
#include <QLabel>
#include <QStyle>
#include <QGroupBox>

#include "uiEnvironment.h"

/* These are primitives for the synthesizer UI
 *
 * each primitive aims to be as self contained as possible.
 * After it's range information is set up, it will
 * write a DSP ready value to a destination variable
 * that the DSP functions can read from directly without
 * any additional processing on their part
 */

class qtDial{
    /* qtDial is a knob that controls 1 synth paramter
     * this class contains a QDial object, and 2 label
     * objects. the first label object is the name
     * of the parameter the dial controls, and the
     * second label displays it's current value
     *
     */
private:
    /*ui objects*/
    //parent widget
    QWidget* parent;
    //QT dial object
    QDial dial;
    //label objects
    QLabel nameLabel;
    QLabel valueLabel;
    //parameter name
    string name;
    //string to be appended to value display
    string suffix;
    //does a suffix need to be added?
    bool suffixFlag;
    stringstream txtBuffer;
    
    /*ui settings*/
    //size in pixels (X&Y) of dial
    int size;
    //object's position on parent
    int posX;
    int posY;
    //dial min and max values
    int uiMin;
    int uiMax;
    //dial starting position
    int uiStart;
    /* These values define how the integer
     * only output of the QDial is translated
     * into float values required by the DSP functions
     */
    int lastVal;
    //min and max float output value
    float valMin;
    float valMax;
    //current output value
    float value;
    //scratch val (to help readability)
    float tempVal;
    //pointer to external destination value
    float* dest;
public:
    qtDial(){
        //set dial notch settings
        dial.setNotchTarget(4.0);
        dial.setNotchesVisible(true);

        //set label formatting
        nameLabel.setAlignment(Qt::AlignCenter);
        valueLabel.setAlignment(Qt::AlignCenter);
    }
    void setDsplyValues(int dSize, int dPosX, int dPosY){
        /* Sets the dial size and position of the knob
         * Args:
         *  ->dSize: The size (x&y) of the QTDial
         *  ->dPosX & dPosY: where the qtDialobject
         *      will be located on the parent widget
         */
        size = dSize;
        posX = dPosX;
        posY = dPosY;

        /*set size & position*/
        //set dial
        dial.setGeometry(0, 0, size, size);
        dial.move(posX, posY);
        //set nameLabel
        nameLabel.setGeometry(0, 0, size, 15);
        nameLabel.move(posX, (posY - 15));
        //set valueLabel
        valueLabel.setGeometry(0, 0, (size), 15);
        valueLabel.move(posX, (posY+size));
    }
    void setUiValues(int min, int max, int start){
        /* Sets the value range of the dial
         * Args:
         *  ->min & max: the minimum & maximum dial values
         *  ->start: dial's starting position
         */
        uiMin = min;
        uiMax = max;
        uiStart = start;

        //set dial step and position
        dial.setMinimum(uiMin);
        dial.setMaximum(uiMax);
        dial.setValue(uiStart);
    }
    void setNameAndParent(string nme, string sfx, QWidget* par){
        /* Sets the object name, value suffix, and QT parent widget
         */
        name = nme;
        suffix = sfx;
        parent = par;
        //set suffix flag (if suffix string is above 0 length)
        suffixFlag = (suffix.length() > 0);

        //set parents
        dial.setParent(parent);
        nameLabel.setParent(parent);
        valueLabel.setParent(parent);

        /*set object names and titles*/

        string work;

        //dial name
        work.assign(name);
        work.append("_DIAL");
        dial.setObjectName(work.c_str());

        //name label
        work.assign(name);
        work.append("_LABEL");
        nameLabel.setObjectName(work.c_str());
        nameLabel.setText(name.c_str());

        //value label
        work.assign(name);
        work.append("_VALUE");
        valueLabel.setObjectName(work.c_str());
    }

    void setScaleValues(float min, float max){
        //sets the floating point min and max
        valMin = min;
        valMax = max;
    }

    void setPointer(float* dst){
        //sets pointer to destination value
        dest = dst;
    }

    float* getPointer(){
        //self explanatory
        return dest;
    }

    void updateValue(){
        //if dial value has changed since last update...
        if(lastVal != dial.value()){
            //transform from (x..y) -> (0..1)
            tempVal = ((float)(dial.value() - uiMin)) / ((float)(uiMax - uiMin));
            //transform (0...1) into (valMin...valMax)
            value = (tempVal * (valMax - valMin)) + valMin;
            //write current value into the value display label
            txtBuffer.str("");
            txtBuffer << value;
            //add the suffix if it exists
            if(suffixFlag){
                txtBuffer << " ";
                txtBuffer << suffix;
            }
            //set value display label
            valueLabel.setText(txtBuffer.str().c_str());
            //write change to terminal
            cout << name << " changed to " << txtBuffer.str() << endl;
            txtBuffer.str("");
            //set last val for comparison next update
            lastVal = dial.value();
            //write value to destination variable
            *dest = value;
        }
    }
};

class qtGroupBox{
    /* This is just a group box that
     * holds other widgets
     * It has a publicly accesible pointer
     * that can be given to child widgets
     */
private:
    /*ui objects*/
    //parent widget
    QWidget* parent;
    //QT dial object
    QGroupBox box;
    
    //box name
    string name;

    //object's position on parent
    int posX;
    int posY;

    //objects size
    int sizeX;
    int sizeY;
public:
    //pointer to parent obj
    QWidget* pointer;
    
    qtGroupBox(){
        pointer = &box;
    }
    void setParent(QWidget* par){
        parent = par;
        box.setParent(parent);
    }

    void setName(string nme){
        name = nme;
        box.setObjectName(name.c_str());
        box.setTitle(name.c_str());
    }
    void setPos(int x, int y){
        posX = x;
        posY = y;
        box.move(posX, posY);
    }
    void setSize(int x, int y){
        sizeX = x;
        sizeY = y;
        box.setGeometry(0, 0, sizeX, sizeY);
    }
};

#include <QRadioButton>
#include <QVBoxLayout>

class qtRadioButton{
    /* qtRadioButton is a radio button box
     * with a variable number of choices
     *
     * output is integer, and is equivalent to
     * (choice# - 1)
     */
private:
    /*ui objects*/
    //parent widget
    QWidget* parent;
    //QGroupBox object
    QGroupBox box;
    //QRadioButton pointer
    QRadioButton * radio;
    //button name pointer
    string * rName;
    //layout object
    QVBoxLayout vbox;
    //number of choices
    int numElements;
    //parameter name
    string name;
    //parent name (for cout)
    string parentName;
    /*ui settings*/
    //object's position on parent
    int posX;
    int posY;
    //size in pixels (X&Y) of dial
    int sizeX;
    int sizeY;
    //values
    int value;
    int* dest;
public:
    qtRadioButton(){
        vbox.addStretch(1);
        vbox.setMargin(0);
        box.setLayout(&vbox);
    }

    void setNumElements(int nEle){
        /* sets the number of elements in
         * this radio button box, and
         * creates the QRadioButton instances
         */

        numElements = nEle;
        //allocate pieces
        radio = new QRadioButton [numElements];
        rName = new string [numElements];
    }

    void setBoxName(string nme){
        /* Sets the name OF THE CONTAINER
         * (not any of the choices)
         */
        name = nme;
        box.setObjectName(name.c_str());
        box.setTitle(name.c_str());
    }

    void setParentName(string nme){
        parentName = nme;
    }

    void setParent(QWidget* par){
        /* Defines the box's parent widget
         */
        parent = par;
        //
        box.setParent(parent);
    }

    void setPos(int x, int y){
        posX = x;
        posY = y;
        //set box position
        box.move(posX, posY);
    }

    void setSize(int x, int y){
        sizeX = x;
        sizeY = y;
        //set box size
        box.setGeometry(0, 0, sizeX, sizeY);
    }

    void setElement(int idx, string nme){
        /* configures one of the
         */
        if(idx >= numElements){
            cout << "can't add " << nme << " at idx " << idx << endl;
            cout << "max is " << (numElements - 1) << endl;
        } else {
            radio[idx].setText(nme.c_str());
            radio[idx].animateClick(150);
            rName[idx].assign(nme.c_str());
            vbox.addWidget(&radio[idx]);
        }
        radio[0].setChecked(true);
    }

    void setPointer(int* dst){
        dest = dst;
    }

    int* getPointer(){
        return dest;
    }

    void updateValue(){
        for(int i=0; i<numElements; i++){
            if(radio[i].isChecked()){
                if(value != i){
                    cout << parentName << " " << name << " changed to " << rName[i] << " " << i << endl;
                    value = i;
                    *dest = value;
                }
            }
        }
        
    }

    ~qtRadioButton(){
        delete [] radio;
        delete [] rName;
    }
};

#endif	/* _UIELEMENTS_H */


```

The oscillator module:

```
/* 
 * File:   oscillatorBank.h
 * Author: blake
 *
 * Created on August 1, 2009, 9:34 PM
 */

#ifndef _OSCILLATORBANK_H
#define	_OSCILLATORBANK_H

#include <cassert>

//ui
#include "uiEnvironment.h"
#include "uiElements.h"

//oscillator classes
#include "waveshapes.h"
#include "rampGen.h"

class analogOscBankGUI{
private:
    //UI elements
    QWidget* parent;
    qtGroupBox oscBox;
    qtDial semi;
    qtDial detune;
    qtRadioButton shape;
    //ui settings
    string name;
    int posX;
    int posY;
public:
    //values
    float semiVal;
    float detuneVal;
    int shapeVal;

    analogOscBankGUI(){
        //init values
        semiVal = 0;
        detuneVal = 0;
        shapeVal = 0;

        oscBox.setSize(200,200);

        //semitone dial setup
        semi.setDsplyValues(50,5,30);
        semi.setUiValues(-36,36,0);
        semi.setNameAndParent("semi", "", oscBox.pointer);
        semi.setPointer(&semiVal);

        assert(&semiVal == semi.getPointer());
        assert(&semiVal != NULL);
        assert(semi.getPointer() != NULL);

        semi.setScaleValues(-36,36);

        //detune dial setup
        detune.setDsplyValues(50,5,120);
        detune.setUiValues(-100,100,0);
        detune.setNameAndParent("detune", "", oscBox.pointer);
        detune.setPointer(&detuneVal);

        assert(&detuneVal == detune.getPointer());
        assert(&detuneVal != NULL);
        assert(detune.getPointer() != NULL);

        detune.setScaleValues(-1,1);

        //waveshape selector setup
        shape.setParent(oscBox.pointer);
        shape.setNumElements(4);
        shape.setBoxName("Wave");
        shape.setSize(55,80);

        shape.setElement(0,"sin");
        shape.setElement(1,"tri");
        shape.setElement(2,"saw");
        shape.setElement(3,"sqr");

        shape.setPos(70, 15);
        shape.setPointer(&shapeVal);

        assert(&shapeVal == shape.getPointer());
        assert(&shapeVal != NULL);
        assert(shape.getPointer() != NULL);
    }
    void setPos(int x, int y){
        /* Set oscillator instance
         * GUI position
         */
        posX = x;
        posY = y;
        //
        oscBox.setPos(posX,posY);
    }
    void setNameAndParent(string nme, QWidget* par){
        /* Oscillator Name, and parent widget
         */
        name = nme;
        parent = par;
        //
        oscBox.setParent(parent);
        oscBox.setName(name);
    }
    void init(){
        cout << "initializing " << name << endl;
    }
    void updateValues(){
        semi.updateValue();
        detune.updateValue();
        shape.updateValue();
    }
};

class analogOscBankDSP{
private:
    //pointer to the controller instance
    analogOscBankGUI * controller;

public:
    //
};



#endif	/* _OSCILLATORBANK_H */


```

And I've attached the result

I'm sure it looks like I'm overcomplicating this, but synth UIs get very complicated very quickly, and this will save me a TON of time down the road.

---

### Post by lisati on 2009-08-14
> **blake82 said:**
> Sorry dwhitney67, my code is normally thoroughly commented :)

I'll comment it out and repost with better explanations of what's going on.

Just a note: "commenting something out" is sometimes seen as something different to providing comments. In the programming style I was taught to comment something out is part of the debugging process and means to temporarily remove a line from what gets compiled by turning into a comment.

---

### Post by blake82 on 2009-08-16
Hi Lisati,

Yeah I know... not sure why I didn't think of that when writing my post :)

---

