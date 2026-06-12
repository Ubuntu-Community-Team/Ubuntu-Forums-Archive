---
title: "Android threading help"
date: 2010-06-22
forum: Programming Talk
---

### Post by antman8969 on 2010-06-22
My android experience has become very frustrating. It seems that the OS isn't thread safe so there are special ways of doing what I want to do, but I can't quite get it down. 

Basically, what I have is a Button and a TextView. When I click that Button, I want it to execute a thread that updates the TextView...this will eventually turn into a stopwatch. 

Here is my task:
```
import android.os.AsyncTask;
import android.widget.TextView;

public class UpdateTimeTask extends AsyncTask<TextView,Integer,String> {

	TextView timeView;
	protected String doInBackground(TextView ...view){
		this.timeView = view[0];
		
		
		return "john";
	}
	
	
	
	protected void onPostExecute(String result){
		timeView.setText(result);
	}
}
```

EDIT: I just fixed the problem. I forgot to delete my otherThread.start() :oops:. But I guess I could still use suggestions on how to do the looping without blocking the UI thread

---

### Post by mainerror on 2010-06-22
I highly recommend you the #android-dev channel on irc.freenode.net.

You'll definitely find help there.

---

### Post by antman8969 on 2010-06-22
> **mainerror said:**
> I highly recommend you the #android-dev channel on irc.freenode.net.

You'll definitely find help there.

thanks, heading over now

---

