---
title: "Java multi-thread application recompile object with make but runs with old values"
date: 2010-04-05
forum: Programming Talk
---

### Post by raequin on 2010-04-05
Hi.  I am working on a simulation in Java, and there is some behavior going on that I cannot understand.  Granted, I'm a mechanical engineer, not a CS student (a fact that is probably made obvious by the code I'm posting below).  The simulation comprises three parts: a controller, a robot, and a 3-d sensor.  Here's the code for the "Simulation" application.

```

class Simulation {
    void go() {
	ThreeDSensor sensorRunner = new ThreeDSensor();
	VSController controllerRunner = new VSController();
	KukaKR15SL robotRunner = new KukaKR15SL();


	Thread sensorThread = new Thread(sensorRunner);
	Thread controllerThread = new Thread(controllerRunner);
	Thread robotThread = new Thread(robotRunner);


	sensorThread.start();
	try {
	    Thread.sleep(1000);  // Give sensorThread time to start in order to catch first triggers
	} catch(InterruptedException ex) {
	    ex.printStackTrace();
	}


	controllerThread.start();
	try {
	    Thread.sleep(1000);  // Give controllerThread time to open the socket for communication with robotThread
	} catch(InterruptedException ex) {
	    ex.printStackTrace();
	}


	robotThread.start();
    }


    public static void main(String[] args) {
	Simulation sim = new Simulation();
	sim.go();
    }
}

```

I guess the big reason I'm using multi-threading is that once this simulation is working I want to be able to just run VSController alone and have it interface with a robot controller and a PC performing image processing.  So with multiple threads I'm sending TCP and UDP messages around just like the final system will.

I have made an object for my VSController that just stores values used by the simulation.  That way I could have them all in one place instead of hunting through methods to change them.  The value I'm currently concerned with is "double noiseThreshold".  Quickly, here is the code for "ControllerSettings.java".

```

class ControllerSettings {
    final double cameraXOffset = 0;  // If > 0 then the origin of the camera CS is not on the center line of the lens
    final double cameraYOffset = 0;  // If > 0 then the origin of the camera CS is not on the center line of the lens
    final double cameraZOffset = 700;  // The distance that must be kept between the camera and the target


    // Error magnitude less than this is disregarded (in centimeters if roundingData else in millimeters)
    final double noiseThreshold = 60;


    final boolean estimatingEndPoints = false;  // If the controller is using two images per cycle then true
    final boolean roundingData = false;
    final boolean using3DData = true;  // How double[] sent from Matlab image processing is used


    /*
     * If the robot controller uses the output of this controller to command 
     * motions in cartesian space then true.  This is used in two places: 1) initial guess of Jacobian,
     * and 2) "commandType" element sent to robot controller.
     */
    final boolean useRobotControllerModel = false;


    final double thetaBumpValueForEstimationOfJacobian = .1;  // Distance each joint is jogged in estimation process
    final double bumpDistance = 50;  // Distance robot moves each time (magnitude of translation in mm)
    final double limitAngular = .5;  // Max amout robot joint will be commanded to rotate (in degrees)
}

```

And here is some pertinent code from "VSController.java".

```

class VSController implements Runnable{
    ControllerSettings cSettings;  // Stores all the preferences used by the controller
    NGN controller;  // This is the controller algorithm.
    int dof;  // The degrees of freedom of the robot being controlled
    KukaSendData ksd;  // This provides communication to the robot.
    protected DatagramSocket socketForVisionSystem = null;
    ImageFeaturesData ifd;  // This parses and stores data from the image system.
    double[] errorVector;  // This is what's acted on by the algorithm

    PrintWriter errorTrackerOut = null;  // For analysis of error vector

    public void run() {
	VSController vsc = new VSController();
	vsc.go();
    }


    public void go() {
	initWriters();
	cSettings = new ControllerSettings();

...

    public boolean isNoise() {
	boolean ret = false;
	double magnitude = 0;
	for (int i = 0; i < errorVector.length; i++) {
	    magnitude += errorVector[i] * errorVector[i];
	}
	magnitude = Math.sqrt(magnitude);
	if (magnitude <= cSettings.noiseThreshold) {
	    System.out.println("VSController: magnitude (of errorVector) = " + magnitude +
			       ", threshold = " + cSettings.noiseThreshold);  // Debug

...

```

Now here's my issue: I change the value for "noiseThreshold" in "ControllerSettings.java" then run make from terminal (makefile code posted below) and rerun "Simulation".  However, despite my changes to "ControllerSettings.java" the value for "noiseThreshold" is not changed, as evidenced by the output on the terminal screen:```
VSController: magnitude (of errorVector) = 6.085046125925263, threshold = 10.0
```  See, that value of 10.0 is what I used to have for noiseThreshold.  I do not know why this value does not update even though I save the java file and execute make in between executions of Simulation.  I would love it if someone could explain this problem to me.

Here's the contents of makefile.

```

JFLAGS = -cp ../Jama\-1\.0\.2.jar:../utils/:/usr/share/java/vecmath\-1\.5\.2.jar:.
JC = javac
.SUFFIXES: .java .class
.java.class:
	$(JC) $(JFLAGS) $*.java

CLASSES = \
	ControllerSettings.java \
	ImageFeaturesData.java \
	KukaKR15SL.java \
	../utils/KukaSendData.java \
	NGN.java \
	Puma560.java \
	Robot.java \
	RobotSettings.java \
	Simulation.java \
	SimulationSettings.java \
	SixRRobot.java \
	Targets.java \
	TargetsSettings.java \
	ThreeDData.java \
	ThreeDSensor.java \
	VSController.java

default: classes

classes: $(CLASSES:.java=.class)

clean:
	$(RM) *.class

```

---

### Post by Reiger on 2010-04-05
Possibly there is an older .class file that prevents the class from being recompiled. Try executing make clean && make.

---

### Post by Some Penguin on 2010-04-05
You're a victim of a compiler optimization called 'constant folding' or 'inlining'.

See [http://stackoverflow.com/questions/377819/are-all-compile-time-constants-inlined](http://stackoverflow.com/questions/377819/are-all-compile-time-constants-inlined) for some details.

---

### Post by raequin on 2010-04-05
Okay, due to the above reply, I saw this explanation about what's causing my problem.

> When the Java compiler sees a reference to a final static primitive or String, it inserts the actual value of that constant into the class that uses it. If you then change the constant value in the defining class but don't recompile the using class, it will continue to use the old value.

I verified that the value updates if I also change something in VSController.java, forcing it to recompile.  I think I will solve this problem by just making the variables in ControllerSettings no longer final (and then recompile VSController to make sure it takes effect!).  Is there another solution?  I saw intern(), but that seems to only apply to Strings.

Thanks.

---

### Post by Some Penguin on 2010-04-05
You could experiment with wrapping it in an accessor method, but without testing I couldn't specify with any certainty that the compiler wouldn't notice that the method returns a constant value and inline it the call.

A more sure solution would be to use a properties file rather than constants embedded in code.

---

### Post by cdekter on 2010-04-06
Why not just do a clean before you recompile? Standard practice...

---

### Post by raequin on 2010-04-06
I will take one of the following courses of action: either change the variables from "final double" to "double," or compile with "make clean && make" instead of just "make"; probably the latter. Thanks.

---

