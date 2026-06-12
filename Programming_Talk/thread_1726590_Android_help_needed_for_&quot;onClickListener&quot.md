---
title: "Android help needed for &quot;onClickListener&quot; demo"
date: 2011-04-11
forum: Programming Talk
---

### Post by youbuntu on 2011-04-11
Hi there. Here is my code:

```

package com.button.click;

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.TextView;

public class MainScreen extends Activity implements OnClickListener {
    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
        TextView showText = (TextView)findViewById(R.id.showText);
        Button genText = (Button) findViewById(R.id.genText);
        genText.setOnClickListener(this);
        
    }

	@Override
	public void onClick(View v) {
		// TODO Auto-generated method stub
        showText.setText("Hello");

	}
}

```

The line: showText.setText("Hello");

Shows an error, and does not work. Could someone suggest what is wrong here? I merely want a label to update when I click the button "genText". Thanks

---

### Post by simeon87 on 2011-04-11
Does it compile at all? showText is a local variable in onCreate so how do you intend to access it in onClick?

---

### Post by youbuntu on 2011-04-11
I have no idea :( would you mind showing me?

thanks


[_EDIT_]

I changed the code to this:

```

package com.button.click;

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;

public class MainScreen extends Activity implements OnClickListener {
    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
        Button genText = (Button) findViewById(R.id.genText);
        genText.setOnClickListener(this);

        
    }

	@Override
	public void onClick(View v) {
		// TODO Auto-generated method stub
        EditText showText = (EditText)findViewById(R.id.showText);
        showText.setText("hello");
		

	}
}

```

And now it seems to work... but is this the correct way?

---

### Post by Shpongle on 2011-04-11
I recently coded an android project for my final year project.

your better off putting your edit text outside the onCreate just under the 
public class MainScreen extends Activity implements OnClickListener line.

Make it private too unless it needs to be public. This way all the required variables are in scope , have the correct access control and it saves code later on. Only create local variables when they are needed

```
package com.button.click;

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;

public class MainScreen extends Activity implements OnClickListener {

    //declare ui components
    private Button genText = (Button) findViewById(R.id.genText);
    private EditText showText = (EditText)findViewById(R.id.showText);


    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
        genText.setOnClickListener(this);

        
    }

	@Override
	public void onClick(View v) {
		// TODO Auto-generated method stub
        showText.setText("hello");
		

	}
}
```

---

### Post by youbuntu on 2011-04-11
> **Shpongle said:**
> I recently coded an android project for my final year project.

your better off putting your edit text outside the onCreate just under the 
public class MainScreen extends Activity implements OnClickListener line.

Make it private too unless it needs to be public. This way all the required variables are in scope , have the correct access control and it saves code later on. Only create local variables when they are needed

```
package com.button.click;

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;

public class MainScreen extends Activity implements OnClickListener {

    //declare ui components
    private Button genText = (Button) findViewById(R.id.genText);
    private EditText showText = (EditText)findViewById(R.id.showText);


    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
        genText.setOnClickListener(this);

        
    }

	@Override
	public void onClick(View v) {
		// TODO Auto-generated method stub
        showText.setText("hello");
		

	}
}
```

So "local" means local access within the method, and not accessible anywhere else, even within that class? And private means accessible anywhere *within* within the class, but not outside it?

I just dusted off my old Java book - didn't realise HOW rusty I have become! :$

---

### Post by Shpongle on 2011-04-12
> **glossywhite said:**
> So "local" means local access within the method, and not accessible anywhere else, even within that class? And private means accessible anywhere *within* within the class, but not outside it?

I just dusted off my old Java book - didn't realise HOW rusty I have become! :$

Private means its not accessible from other classes by using  MyClass.myvariable , you can only get at from another class it by using a getter method like 

getVar(){
  return myvariable;
}


your correct about local , its to do with the scope. You can still define them at the top and then initialize them in the onCreate method. But you wont have to re define them anywhere else.

---

### Post by youbuntu on 2011-04-13
> **Shpongle said:**
> Private means its not accessible from other classes by using  MyClass.myvariable , you can only get at from another class it by using a getter method like 

getVar(){
  return myvariable;
}


your correct about local , its to do with the scope. You can still define them at the top and then initialize them in the onCreate method. But you wont have to re define them anywhere else.

Dude, I did what you suggested but I just get a blank screen with no elements...

```

package com.on.click;

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;

public class ScreenOne extends Activity implements OnClickListener {
	private Button setText = (Button)findViewById(R.id.setText);
	private EditText showText = (EditText)findViewById(R.id.showText);
    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
        setText.setOnClickListener(this);
    }
	@Override
	public void onClick(View v) {
		// TODO Auto-generated method stub
		showText.setText("Clicked!");
	}
}

```

---

### Post by unknownPoster on 2011-04-13
> **youbuntu said:**
> 

I just dusted off my old Java book - didn't realise HOW rusty I have become! :$

I believe this is why many people recommended that you go over basic programming in your other thread rather than undertaking such a significant task like Android Development.

---

### Post by youbuntu on 2011-04-13
> **unknownPoster said:**
> I believe this is why many people recommended that you go over basic programming in your other thread rather than undertaking such a significant task like Android Development.

Agreed :)

However, this IS basic programming!

---

### Post by Shpongle on 2011-04-27
```
package com.on.click;

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;

public class ScreenOne extends Activity implements OnClickListener {

        // declare ui components
	private Button Btn1;
	private EditText Textbox;

    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
       
        //get ui component references
        Btn1 = (Button)findViewById(R.id.setText);
	Textbox showText = (EditText)findViewById(R.id.showText);

        // add listeners
        Btn1.setOnClickListener(this);
    }
	@Override
	public void onClick(View v) {
		// TODO Auto-generated method stub
		Textbox.setText("Clicked!");
	}
}
```

this should work now, I was tired the last time , sorry.

---

