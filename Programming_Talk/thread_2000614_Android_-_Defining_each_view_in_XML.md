---
title: "Android - Defining each view in XML"
date: 2012-06-09
forum: Programming Talk
---

### Post by PaulM1985 on 2012-06-09
I have tried and googled this but I must be searching for the wrong thing.  I am developing a poker game and in normal Java I would have a panel that would overlay my main panel containing information about each player.  It would contain some label with game info, their cards etc.  For Android dev, all I can find is how to develop my application using my:
```

        setContentView(R.layout.main);

```
where that is the only layout for the activity.

Obviously, I don't want to have to define each player's game state control in the main.xml since it would end up with lots of copied code.  I thought I could place down custom controls (I think the Android equivalent are Views) and define the layouts of those in xml.

Does anyone know if this is possible?  It seems to me to be something that must be really common which is why I think I must be searching for the wrong things, or because it is late and I am tired and I am not reading properly :-).

Paul

---

### Post by PaulM1985 on 2012-06-10
Ok, I think I have done it.  What I should have been doing is define my separate "View" as a type of layout. Here is a quick example:

In my main xml which is loaded by the activity:
```

<android.test
	     		android:id="@+id/test_button"
	     		android:layout_height="wrap_content"
	    		android:layout_width="wrap_content"
	     		 />

```

In my test.xml:
```

<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >
	    	<Button
			    android:id="@+id/raise_button"
	     		android:layout_height="wrap_content"
	    		android:layout_width="wrap_content"
	     		android:text="@string/restart_game" />
</FrameLayout>

```

In my test class:
```

package android;

import android.app.Activity;
import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Paint;
import android.util.AttributeSet;
import android.view.View;
import android.widget.LinearLayout;

public class test extends LinearLayout {

	public test(Context context, AttributeSet attrs) {
		super(context, attrs);
		
                // Binds the layout to this
		((Activity)getContext())
        .getLayoutInflater()
        .inflate(R.layout.test, this, true);

	}
}

```

Hope this helps anyone with the same problem.

Paul

---

