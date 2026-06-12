---
title: "Android HTTP request problems."
date: 2010-04-27
forum: Programming Talk
---

### Post by Jekshadow on 2010-04-27
I have a class to fetch a JSON page from the web, and it seems to return random data, yet I can see the page fine in any web browser and via telnet/nc.

The class:
```
import java.io.ByteArrayOutputStream;
import java.io.IOException;
import java.io.InputStream;
import org.apache.http.HttpEntity;
import org.apache.http.HttpResponse;
import org.apache.http.StatusLine;
import org.apache.http.client.ClientProtocolException;
import org.apache.http.client.HttpClient;
import org.apache.http.client.methods.HttpGet;
import org.apache.http.impl.client.DefaultHttpClient;

public class Downloader {
	public String url;
	
	public Downloader(String s_url) {
		url = s_url;
	}
	
	public String fetchToString() {
		HttpClient client = new DefaultHttpClient();
        HttpGet request = new HttpGet(url);
        request.setHeader("User-Agent", "StoqDeq (1.0/bot)");
        HttpResponse response;
		try {
			response = client.execute(request);
		} catch (ClientProtocolException e2) {
			return "Couldn't execute request (protocol)";
		} catch (IOException e2) {
			return "Couldn't execute request (io)";
		}
        
        // Check if server response is valid
        StatusLine status = response.getStatusLine();
        if (status.getStatusCode() != 200) {
	        	
        }
        
        // Pull content stream from response
        HttpEntity entity = response.getEntity();
        InputStream inputStream;
        
        
		try {
			inputStream = entity.getContent();
		} catch (IllegalStateException e1) {
			return "Couldn't get entity context (state)";
		} catch (IOException e1) {
			return "Couldn't get entity context (io)";
		}

        ByteArrayOutputStream content = new ByteArrayOutputStream();

        // Read response into a buffered stream
        int readBytes = 0;
        byte[] sBuffer = new byte[100000];
        try {
			while ((readBytes = inputStream.read(sBuffer)) != -1) {
				content.write(sBuffer, 0, readBytes);
			}
		} catch (IOException e) {
			return "Couldn't read...";
		}
		
		String ret = String.valueOf(content.toByteArray());
		
        // Return result from buffered stream
        return ret;
	}
}

```

---

### Post by Some Penguin on 2010-04-27
One thing that comes to mind is I don't see any references to character encoding.

You're using httpclient-4.x, correct?

If you want a String from an HTTPEntity, you could just invoke the toString() method  from org.apache.http.util.EntityUtils.

---

