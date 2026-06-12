---
title: "[ANDROID] Drop_caches by android app doesn't work"
date: 2013-04-09
forum: Programming Talk
---

### Post by punticci on 2013-04-09
Hi, I've made this script but doesn't work:
```

package com.mkyong.android;
 
import android.annotation.SuppressLint;
import android.app.Activity;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.Toast;
import java.io.IOException;
import com.example.toast.R;
 
public class MainActivity extends Activity {
 
	private Button button;
 
	public void onCreate(Bundle savedInstanceState) {
		final Runtime runtime = Runtime.getRuntime();
		try {
			runtime.exec("su");
		}
		catch (IOException e) {
			e.printStackTrace();
		}
		super.onCreate(savedInstanceState);
		setContentView(R.layout.tab1);
	
		
		button = (Button) findViewById(R.id.button1);
        button.setOnClickListener(new OnClickListener() {
            @SuppressLint("SdCardPath")
			@Override
            public void onClick(View arg0) {
            	final Runtime runtime = Runtime.getRuntime();
        		try {
        			runtime.exec("echo 3 > /proc/sys/vm/drop_caches");
        			Toast.makeText(MainActivity.this, "Script lanciato con successo, memoria svuotata.", Toast.LENGTH_LONG).show();
        		}
        		catch (IOException e) {
        			e.printStackTrace();
        		}
            }
        });
	}
}

```
Doesn't free the RAM memory :( but via terminal emulator goes.. what's wrong?

---

### Post by punticci on 2013-04-09
Nobody? :(

---

### Post by mörgæs on 2013-04-09
Please don't bump a thread.

---

### Post by punticci on 2013-04-10
I'm so sorry but i can't find a way out and i need help :(

---

