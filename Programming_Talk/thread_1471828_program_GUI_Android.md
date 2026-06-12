---
title: "program GUI Android"
date: 2010-05-03
forum: Programming Talk
---

### Post by gotenks05 on 2010-05-03
Hello, I got a Motorola Droid recently and after looking around for a bit, I decided to try and make an app for the Android.  I am familiar with J2SE, so this is not my first time with Java, but it is my first time programming for a platform other than laptop/desktop computers.  Basically, I've got a program already written in Java which calculates the Actual Storage capacity of secondary storage devices ranging from KB to YB and I want to port it to the Android OS.  I have installed the Android SDK onto my computer and already created the GUI Appearance for the Android OS using XML.  How I plan to have it work is that the user enters data in one textfield, then they select a unit from a ComboBox, which I learned were called spinners on the Android.  The spinner ranges from KB to YB for the selection.  After making the selection, the user press a button labelled "Calculate" and the results will appear in a read-only text-field above the button.  Since I made the GUI using XML,  I know that I will need to take a different route to get things to work than what I could have done in J2SE.  Luckily, the formulas needed for the port were in a separate class file inside the executable jar, which was compiled in Java 1.5, so I am hoping that I can use that class file to do the actual calculations.

the source for the class file containing the formulas looks like this:

```
**
*  The Storage class contains methods
*  that calculate the actual storage cacpacity
*  of secondary storage devices, without taking
*  Filesystems into account.
*/

public class Storage
{
	double ListedStorage;

	/**
	*  The setStorage method accepts an argument stored in the 		*  ListedStorage field.
	*/ 
	public void setStorage(double store)
	{
		ListedStorage = store;
	}

	/**
	*  The getStorage method returns the value of the value stored in
	*  the ListedStorage field.
	*/
	public double getStorage()
	{
		return ListedStorage;
	}

	/**
	*  The getKB method calculates the actual storage
	*  in the Kilobytes unit by dividing the product of the
	*  ListedStorage field and 1,000 by 1024.
	*/
	public double getKB()
	{
		return (ListedStorage * 1000)/1024;
	}

	/**
	*  The getMB method calculates the actual storage
	*  in the Megabytes unit by dividing the product of the
	*  ListedStorage field and 1,000^2 by 1024^2.
	*/
	public double getMB()
	{
		return (ListedStorage * Math.pow(1000, 2))/Math.pow(1024, 2);
	}

	/**
	*  The getGB method calculates the actual storage
	*  in the Gigabytes unit by dividing the product of the
	*  ListedStorage field and 1,000^3 by 1024^3.
	*/
	public double getGB()
	{
		return (ListedStorage * Math.pow(1000, 3))/Math.pow(1024, 3);
	}

	/**
	*  The getTB method calculates the actual storage
	*  in the Terabytes unit by dividing the product of the
	*  ListedStorage field and 1,000^4 by 1024^4.
	*/
	public double getTB()
	{
		return (ListedStorage * Math.pow(1000, 4))/Math.pow(1024, 4);
	}

	/**
	*  The getPB method calculates the actual storage
	*  in the Petabytes unit by dividing the product of the
	*  ListedStorage field and 1,000^5 by 1024^5.
	*/
	public double getPB()
	{
		return (ListedStorage * Math.pow(1000, 5))/Math.pow(1024, 5);
	}

	/**
	*  The getEB method calculates the actual storage
	*  in the Exabytes unit by dividing the product of the
	*  ListedStorage field and 1,000^6 by 1024^6.
	*/
	public double getEB()
	{
		return (ListedStorage * Math.pow(1000, 6))/Math.pow(1024, 6);
	}

	/**
	*  The getZB method calculates the actual storage
	*  in the Zetabytes unit by dividing the product of the
	*  ListedStorage field and 1,000^7 by 1024^7.
	*/
	public double getZB()
	{
		return (ListedStorage * Math.pow(1000, 7))/Math.pow(1024, 7);
	}

	/**
	*  The getYB method calculates the actual storage
	*  in the Yottabytes unit by dividing the product of the
	*  ListedStorage field and 1,000^8 by 1024^8.
	*/
	public double getYB()
	{
		return (ListedStorage * Math.pow(1000, 8))/Math.pow(1024, 8);
	}
}
```

The xml file controlling the appearance looks like this:

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >

<!-- the following creates a textfield -->
<EditText android:id="@+id/size"
	android:layout_width="fill_parent"
	android:layout_height="wrap_content"
	android:text="@string/message"
/>

<!-- the following creates a combobox -->
<Spinner android:id="@+id/spinner"
	android:layout_width="fill_parent"
	android:layout_height="wrap_content"
	android:prompt="@string/choices"
/>

<!-- the following creates another textfield -->
<EditText android:id="@+id/result"
	android:layout_width="fill_parent"
	android:layout_height="wrap_content"
	android:text="@string/result"
/>

<!-- the following creates a button -->
<Button android:id="@+id/submit"
	android:layout_width="fill_parent"
	android:layout_height="wrap_content"
	android:text="@string/submit_text"
/>
</LinearLayout>


```

This is what the strings.xml file looks like:

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="app_name">Actual Storage</string>
    <string name="choices">Select a unit</string>
    <string-array name="choices_array">
	<item>kb</item>
	<item>mb</item>
	<item>gb</item>
	<item>tb</item>
	<item>pb</item>
	<item>eb</item>
	<item>zb</item>
	<item>yb</item>
    </string-array>
    <string name="message">Enter a Size</string>
    <string name="submit_text">Calculate</string>
    <string name="result">results</string>
</resources>

```

To show you that the GUI has not been programmed yet, here is the source of the main Java file:

```
package com.Actual.android;

import android.app.Activity;
import android.os.Bundle;

public class ActualStorageActivity extends Activity
{
    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
    }
}

```

Yes, I have not done anything to make the GUI work, because I do not want to get this done wrong because of trying to implement things the same way as J2SE.  So, essentially, I need the Spinner to work properly, setup a listener for the button to put the data into the methods provided by the external Java class, and make the final textfield readonly, in order to display the results.

I am including an image of the GUI, in order for you to see what I have.  Also, I will include the executable JAR file for the J2SE version, so you can tell what I am trying to do in the interface, with a few differences of course.

---

### Post by gotenks05 on 2010-05-04
Okay, after searching around long enough, I finally got close to what I wanted, but it does not work out.  When I run the app, I do not see any results of the math in the final textfield, which should be a readonly field.

Here is the updated source that came from my discoveries:

```
package com.Actual.android;

import android.app.Activity;
import android.os.Bundle;
import android.widget.*;
import android.view.*;
public class ActualStorageActivity extends Activity
{
    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
	final Spinner selection = (Spinner)findViewById(R.id.spinner);
	ArrayAdapter adapter = ArrayAdapter.createFromResource(this, R.array.choices_array, android.R.layout.simple_spinner_dropdown_item);

	adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item);

	selection.setAdapter(adapter);

	
	EditText size = (EditText)findViewById(R.id.size);
	EditText result = (EditText)findViewById(R.id.result);
	result.setCursorVisible(false);

	Button calculate = (Button)findViewById(R.id.submit);

	calculate.setOnClickListener(new View.OnClickListener() {
	public void onClick(View v)
	{

		EditText size = (EditText)findViewById(R.id.size);
		EditText result = (EditText)findViewById(R.id.result);
		Storage capacity = new Storage();
		String initial = size.getText().toString();
		String unit = (String)selection.getSelectedItem();
		String end;
		double convert = Double.parseDouble(initial);
		capacity.setStorage(convert);

		if (unit == "KB")
		{
			end = Double.toString(capacity.getKB());
			result.setText(end);
		}

		else if (unit == "MB")
		{
			end = Double.toString(capacity.getMB());
			result.setText(end);

		}

		else if (unit == "GB")
		{
			end = Double.toString(capacity.getGB());
			result.setText(end);

		}

		else if (unit == "TB")
		{
			end = Double.toString(capacity.getTB());
			result.setText(end);

		}

		else if (unit == "PB")
		{
			end = Double.toString(capacity.getPB());
			result.setText(end);

		}

		else if (unit == "EB")
		{
			end = Double.toString(capacity.getEB());
			result.setText(end);

		}

		else if (unit == "ZB")
		{
			end = Double.toString(capacity.getZB());
			result.setText(end);

		}

		else if (unit == "YB")
		{
			end = Double.toString(capacity.getYB());
			result.setText(end);

		}
	}
		
	});
    }
}

```

---

