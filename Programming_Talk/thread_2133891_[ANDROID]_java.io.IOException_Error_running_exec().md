---
title: "[ANDROID] java.io.IOException: Error running exec(). Command"
date: 2013-04-09
forum: Programming Talk
---

### Post by punticci on 2013-04-09
Hi people.. I've created an android application that, when a button is pressed, start a shell. The shell, just for trying if the app goes, write a file.txt with a text insied. Well the problem is the MainActivity.java in Android App.. This is the code:
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
 
		super.onCreate(savedInstanceState);
		setContentView(R.layout.tab1);	
 
		button = (Button) findViewById(R.id.button1);
        button.setOnClickListener(new OnClickListener() {
            @SuppressLint("SdCardPath")
			@Override
            public void onClick(View arg0) {
                Process p=null;
                try {
                    p = new ProcessBuilder()
                    .command("/sdcard/scritturafile.sh")
                    .start();
                } catch (IOException e) {
                    e.printStackTrace();
                } finally {
                    if(p!=null) p.destroy();
                }
            }
        });
	}
}

```
Seems good. I've got not errors but nothing goes XD. This is the log:
```

[COLOR=#555555][FONT=Monaco]04-09 17:33:38.323: W/System.err(15320): java.io.IOException: Error running exec(). Command: [/sdcard/scritturafile.sh] Working Directory: null Environment: [EMULATED_STORAGE_SOURCE=/mnt/shell/emulated, TERM=linux, ANDROID_SOCKET_zygote=9, ANDROID_STORAGE=/storage, ANDROID_BOOTLOGO=1, EXTERNAL_STORAGE=/storage/emulated/legacy, ANDROID_ASSETS=/system/app, ANDROID_CACHE=/cache, PATH=/sbin:/vendor/bin:/system/sbin:/system/bin:/system/xbin, ASEC_MOUNTPOINT=/mnt/asec, LOOP_MOUNTPOINT=/mnt/obb, BOOTCLASSPATH=/system/framework/core.jar:/system/framework/core-junit.jar:/system/framework/bouncycastle.jar:/system/framework/ext.jar:/system/framework/framework.jar:/system/framework/telephony-common.jar:/system/framework/mms-common.jar:/system/framework/android.policy.jar:/system/framework/services.jar:/system/framework/apache-xml.jar, EMULATED_STORAGE_TARGET=/storage/emulated, TERMINFO=/system/etc/terminfo, ANDROID_DATA=/data, LD_LIBRARY_PATH=/vendor/lib:/system/lib, ANDROID_ROOT=/system, ANDROID_PROPERTY_WORKSPACE=8,49152][/FONT][/COLOR]

```
I can't fix it :( Any ideas?

---

