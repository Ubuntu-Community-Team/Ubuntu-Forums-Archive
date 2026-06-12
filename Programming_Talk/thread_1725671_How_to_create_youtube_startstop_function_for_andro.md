---
title: "How to create youtube start/stop function for android video recording function? HELP!"
date: 2011-04-10
forum: Programming Talk
---

### Post by imso on 2011-04-10
Is there a way to get the entire surfaceView screen to function like a button which start/atop a video recording process whenever it sees fit by the user? The function is somewhat similar to youTube's start/stop play function but instead this time it is used to start/stop the video recording process. 

Is the code suppose to be coded in the .xml file or my .java file to accomplish the task? Sorry i'm rather new to android/java and given only 6 more weeks to finish this assignment by my lecturer to complete an app which act like a car blackbox yet i'm a total beginner in programming... :confused: Any help would be appreciated... Thanks in advance...

This is what i tried so far, can someone guide me i'm really in a desperate situation, PLEASE HELP ME :'(

```
public class CameraTest extends Activity implements SurfaceHolder.Callback {
   
   private static final String TAG = "Exception";
   
   public static SurfaceView surfaceView;
   public static SurfaceHolder surfaceHolder;
   public static Camera camera;
   public static boolean previewRunning;
    
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
        
        surfaceView = (SurfaceView)findViewById(R.id.surface_camera);
        surfaceHolder = surfaceView.getHolder();
        surfaceHolder.addCallback(this);
        
        surfaceHolder.setType(SurfaceHolder.SURFACE_TYPE_PUSH_BUFFERS);
        
        Button btnStart = (Button) findViewById(R.id.button4);
        btnStart.setOnClickListener(new View.OnClickListener() 
        {
           public void onClick(View v)
           {
              startService(new Intent(getApplicationContext(), ServiceRecording.class));
           }
        });
        
        Button btnStop = (Button) findViewById(R.id.button5);
        btnStop.setOnClickListener(new View.OnClickListener() 
        {
           public void onClick(View v)
           {
              stopService(new Intent(getApplicationContext(), ServiceRecording.class));
           }
        });
    }
    
    @Override
    public void surfaceCreated(SurfaceHolder holder) {
       camera = Camera.open();
       if (camera != null) {
          Camera.Parameters params = camera.getParameters();
          camera.setParameters(params);
       }
       else {
          Toast.makeText(getApplicationContext(), "Camera not available!", Toast.LENGTH_LONG).show();
          finish();
       }
    }
    
    @Override
    public void surfaceChanged(SurfaceHolder holder, int format, int width, int height) {
       if (previewRunning) {
          camera.stopPreview();
       }
       
       Camera.Parameters p = camera.getParameters();
       p.setPreviewSize(320, 240);
       p.setPreviewFormat(PixelFormat.JPEG);
       camera.setParameters(p);
       
       try {
             camera.setPreviewDisplay(holder);
             camera.startPreview();
             previewRunning = true;
       }
       catch (IOException e) {
          Log.e(TAG,e.getMessage());
          e.printStackTrace();
       }
    }
    
    @Override
    public void onResume(){
       super.onResume();
       
    }
    
    @Override
    public void surfaceDestroyed(SurfaceHolder holder){
          camera.stopPreview();
          previewRunning = false;
          camera.release();
    }
}
```
 My serviceRecording.java file
```
public class ServiceRecording extends Service {

	@Override
	public IBinder onBind(Intent intent) {
		// TODO Auto-generated method stub
		return null;
	}
   
	private SurfaceView surfaceView;
	private SurfaceHolder surfaceHolder;
	public static Camera ServiceCamera;
	private boolean RecordingStatus;
	private MediaRecorder mediaRecorder;
    private final int maxDurationInMs = 20000;
    
    private static final String TAG = "Exception";
    
    @Override
    public void onCreate() {
    	super.onCreate();
    	
    	RecordingStatus = false;
    	ServiceCamera = CameraTest.MainCamera;
    	surfaceView = CameraTest.surfaceView;
    	surfaceHolder = CameraTest.surfaceHolder;
    }
    
    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
    	super.onStartCommand(intent, flags, startId);
    	if (RecordingStatus == false)
    		startRecording();
    
    	return START_STICKY;
    }
    
    @Override
    public void onDestroy() {
    	super.onDestroy();
    
    	stopRecording();
    	RecordingStatus = false;
    }	
    
    public boolean startRecording(){
    	try {
    			Toast.makeText(getBaseContext(), "Recording Started", Toast.LENGTH_SHORT).show();
    			try{
    				ServiceCamera.unlock();
    			}
    			catch(Exception e){
    				
    				ServiceCamera.reconnect();	
    			}
    			
    			mediaRecorder = new MediaRecorder();
    			
    			mediaRecorder.setCamera(ServiceCamera);
    			
    			mediaRecorder.setAudioSource(MediaRecorder.AudioSource.MIC);
    
    			mediaRecorder.setVideoSource(MediaRecorder.VideoSource.CAMERA);
    
    			mediaRecorder.setOutputFormat(MediaRecorder.OutputFormat.DEFAULT);
    				
    			mediaRecorder.setMaxDuration(maxDurationInMs);
    				 				
    				mediaRecorder.setAudioEncoder(MediaRecorder.AudioEncoder.DEFAULT);
    				
    				mediaRecorder.setVideoEncoder(MediaRecorder.VideoEncoder.DEFAULT);
    				
    				//mediaRecorder.setOutputFormat(MediaRecorder.OutputFormat.DEFAULT);
    				DateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH_mm_ss");
    				Date date = new Date();
    				File directory = new File(Environment.getExternalStorageDirectory() + "/VideoList");
    				
    				if(!(directory.exists()))
    					directory.mkdir();
    					
    				File FileSaved = new File(Environment.getExternalStorageDirectory() + "/VideoList", dateFormat.format(date) + ".3gp");
    				mediaRecorder.setOutputFile(FileSaved.getPath());
    				
    				mediaRecorder.setVideoSize(surfaceView.getWidth(),surfaceView.getHeight());
    				
    				//mediaRecorder.setVideoFrameRate(videoFramesPerSecond);
    				
    				mediaRecorder.setPreviewDisplay(surfaceHolder.getSurface());
    							
    				mediaRecorder.prepare();
    				mediaRecorder.start();	
    				
    				RecordingStatus = true;
    				
    				return true;						
    	} 
    	
    	catch (IllegalStateException e) {
    		Log.d(TAG,e.getMessage());
    		e.printStackTrace();
    		return false;
    	} 
    	catch (IOException e) {
    		Log.d(TAG,e.getMessage());
    		e.printStackTrace();
    		return false;
    	}
    }
    
    public void stopRecording() {
    	Toast.makeText(getBaseContext(), "Recording Stopped", Toast.LENGTH_SHORT).show();	
    	mediaRecorder.stop();
    	
    	try {
    		ServiceCamera.reconnect();
		} catch (IOException e) {
			e.printStackTrace();
		}
    	RecordingStatus = false;
    }
    }
```

My .xml file 
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout
xmlns:android="http://schemas.android.com/apk/res/android"
android:id="@+id/frameLayout1"
android:layout_width="match_parent"
android:layout_height="match_parent"
>
    <RelativeLayout 
   		android:id="@+id/relativeLayout1"
     	android:layout_height="match_parent" 
    	android:layout_width="match_parent">
        <Button 
        android:text="Video" 
        android:id="@+id/button1" 
        android:layout_width="wrap_content" 
        android:layout_height="wrap_content"
        ></Button>
        <Button 
        android:text="Setting" 
        android:id="@+id/button2" 
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"
        android:layout_below="@+id/button1"
        ></Button>
        <Button 
        android:text="Back" 
        android:id="@+id/button3" 
        android:layout_width="wrap_content" 
        android:layout_height="wrap_content"
        android:layout_below="@+id/button2"
        ></Button>
        <Button 
        android:text="Start" 
        android:id="@+id/button4" 
        android:layout_width="wrap_content" 
        android:layout_height="wrap_content"
        android:layout_below="@+id/button3"
        ></Button>
        <Button 
        android:text="Stop" 
        android:id="@+id/button5" 
        android:layout_width="wrap_content" 
        android:layout_height="wrap_content"
        android:layout_below="@+id/button4"
        ></Button>
        <SurfaceView 
        android:id="@+id/surface_camera" 
        android:layout_width="480dp" 
        android:layout_height="320dp"
        android:layout_toRightOf="@+id/button2"
      
        ></SurfaceView>
        <TextView 
        android:text="TextView" 
        android:id="@+id/textView1" 
        android:layout_width="wrap_content" 
        android:layout_height="wrap_content"
        android:layout_toRightOf="@+id/button2"
        ></TextView>
        <TextView 
        android:text="TextView" 
        android:id="@+id/textView2" 
        android:layout_width="wrap_content" 
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        ></TextView>
        <TextView 
        android:text="TextView" 
        android:id="@+id/textView2" 
        android:layout_width="wrap_content" 
        android:layout_height="wrap_content"
        android:layout_alignParentRight="true"
        ></TextView>
        
         </RelativeLayout>
</FrameLayout>
```

---

### Post by imso on 2011-04-14
Can someone help guide me with this? I really need some advice here, I've tried many xda-developer and other such forums to help me on this issue but none of my post receive any advice or help of some sort...:confused:

---

