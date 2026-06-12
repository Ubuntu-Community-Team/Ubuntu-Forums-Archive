---
title: "How do i capped my maximum directory storage space in SD Android? PLEASE HELP!!!"
date: 2011-04-09
forum: Programming Talk
---

### Post by imso on 2011-04-09
Question 1: Presumingly i wanted to allocate only 1GB of space to store my videos in a particular self declared directory how should i do it?

Question 2: And i wanted my directory to capped at 1GB after which how is it going to auto-delete the oldest video file in that directory once its about to reach 1GB?

Sorry i'm kinna new in java/android and currently creating an car blackbox app can someone help me... Thanks in advance :)

This is what I have tried so far can someone tell me how should i implement the above functions into my mainActivity and RecordingService.java files:

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

My RecordingService.java Service file
```
public class ServiceRecording extends Service {

   @Override
   public IBinder onBind(Intent intent) {
      // TODO Auto-generated method stub
      return null;
   }
   
   private SurfaceView surfaceView;
   private SurfaceHolder surfaceHolder;
   private Camera camera;
   private boolean recordingStatus;
   private MediaRecorder mediaRecorder;
   private final int maxDurationInMs = 20000;
    
    private static final String TAG = "Exception";
    
    @Override
    public void onCreate() {
       super.onCreate();
       
       recordingStatus = false;
       camera = CameraTest.camera;
       surfaceView = CameraTest.surfaceView;
       surfaceHolder = CameraTest.surfaceHolder;
    }
    
    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
       super.onStartCommand(intent, flags, startId);
       if (recordingStatus == false)
          startRecording();
    
       return START_STICKY;
    }
    
    @Override
    public void onDestroy() {
       super.onDestroy();
    
       stopRecording();
       //camera.stopPreview();
       recordingStatus = false;
       //camera.release();
    }   
    
    public boolean startRecording(){
       try {
             Toast.makeText(getBaseContext(), "Recording Started", Toast.LENGTH_SHORT).show();
             try{
                camera.unlock();
             }
             catch(Exception e){
                
                camera.reconnect();   
             }
             
             mediaRecorder = new MediaRecorder();
             
             mediaRecorder.setCamera(camera);
             
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
                
                recordingStatus = true;
                
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
         camera.reconnect();
      } catch (IOException e) {
         // TODO Auto-generated catch block
         e.printStackTrace();
      }
       recordingStatus = false;
    }
}
```

---

### Post by slavik on 2011-04-10
try asking on the xda-developers forum.

---

### Post by imso on 2011-04-10
I tried there too but no one answered... :(

---

