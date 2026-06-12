---
title: "Error message &quot;Scanner cannot be resolved into a class&quot; in  Java."
date: 2014-02-10
forum: Programming Talk
---

### Post by Harrison_Selle on 2014-02-10
**Edit:** oops meant to title "Scanner object cannot be resolved into a type"

I am trying to use the Scanner object in Java for a homework assignment. 
Here's the program. It's written on notepad but compiled and run on a server belonging to the school.
```
import java.util.Scanner;
class Palindrome
{
public static boolean isPalindrome(String s)
{
    if (s.length() <= 1)
    {
        return true; //base case
    }
    else if(s.charAt(s.length()) == s.charAt(0))
    {
        isPalindrome(s.substring(1, s.length() - 1)); //passes a new substring excluding first and last character
    }
}
public static void main (String [] args)
{
    System.out.println("Please input a string to see if it is a palindrome!");
    Scanner keyboard = new Scanner(System.in);
    String input = keyboard.nextLine();
    
    if (isPalindrome(input) == true)
    {
        System.out.println(input + " is a palindrome!");
    }
    else
    {
        System.out.println(input + " is not a palindrome!");
    }
}
}

```

I was using Scanner without any problems last semester but upon compiling the program on the schools server I got this error.
Here's what happens when I type the command "java -version"

```
java version "1.5.0"
gij (GNU libgcj) version 4.2.4 (Ubuntu 4.2.4-1ubuntu3
```)

And here's "javac -version"

```
gcj-4.2 (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
```

The javac command only showing some ubuntu info troubles me, but I don't understand how that could be a problem on my end, seeing as how the programs are compiled and run on a different machine. I messed around with Eclipse a while ago, did I screw something up with the version of the compiler? I don't see how that would affect anything outside of Eclipse though...
Thanks for the help.

---

### Post by cariboo on 2014-02-10
Moved to Programming Talk.

---

### Post by ofnuts on 2014-02-11
It may depend on the class path, even though I would expect the java compiler to set up the class path properly to cover the standard packages. But here you aren't really using the standard Java compiler.

Also check which version of Java is really implemented in the compiler, the Scanner class appeared in 1.5.

---

### Post by Harrison_Selle on 2014-02-11
How would i go about checking which version? Also i remember messing with the system variable "path" to set up eclipse. Could this have something to do with it?
Here's the variable:

C:\Program Files (x86)\NVIDIA Corporation\PhysX\Common;C:\Program Files (x86)\Intel\iCLS Client\;C:\Program Files\Intel\iCLS Client\;%SystemRoot%\system32;%SystemRoot%;%SystemRoot%\System32\Wbem;%SYSTEMROOT%\System32\WindowsPowerShell\v1.0\;C:\Program Files (x86)\Windows Live\Shared;C:\Program Files\Intel\Intel(R) Management Engine Components\DAL;C:\Program Files\Intel\Intel(R) Management Engine Components\IPT;C:\Program Files (x86)\Intel\Intel(R) Management Engine Components\DAL;C:\Program Files (x86)\Intel\Intel(R) Management Engine Components\IPT;C:\Program Files (x86)\Intel\OpenCL SDK\2.0\bin\x86;C:\Program Files (x86)\Intel\OpenCL SDK\2.0\bin\x64;C:\Program Files\Intel\WiFi\bin\;C:\Program Files\Common Files\Intel\WirelessCommon\;C:\Program Files\jEdit;C:\Program Files (x86)\OpenNI\Bin;C:\Program Files (x86)\PrimeSense\NITE\bin

---

### Post by ofnuts on 2014-02-11
"class path", not "path".

---

### Post by Harrison_Selle on 2014-02-11
Okay, here is CLASSPATH:

C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar

---

### Post by ofnuts on 2014-02-11
Depends on the contents of the .JAR. If you list the contents (unzip -ml or else, JAR are basically ZIP files), is here a /java/util/Scanner.class in it?

---

### Post by Harrison_Selle on 2014-02-12
So i'm getting this error message when I try to extract the org.OpenNi.jar with WinRar 

!   Cannot create folder C:\Program Files (x86)\OpenNI\Bin\org.OpenNI

When I try to extract it to somewhere else i get this error.

!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create folder META-INF
    Access is denied.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create META-INF\MANIFEST.MF
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create folder org
    Access is denied.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create folder org\OpenNI
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ActiveHandDirectionEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ActiveHandEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\AlternativeViewpointCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\AlternativeViewpointCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\AntiFlickerCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\AntiFlickerCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\AudioGenerator$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\AudioGenerator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\AudioMetaData.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\BoundingBox3D.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\CalibrationProgressEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\CalibrationProgressStatus.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\CalibrationStartEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Capability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\CapabilityBase.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Codec.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\CodecID.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Context$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Context$2.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Context$3.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Context.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Cropping.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\CroppingCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\CroppingCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\DepthGenerator$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\DepthGenerator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\DepthMap.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\DepthMetaData.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Device.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\DeviceIdentificationCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Direction.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\EnumerationErrors.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ErrorStateCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ErrorStateCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ErrorStateEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\EventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\FieldOfView.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\FrameSyncCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\FrameSyncCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GeneralException.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GeneralIntCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GeneralIntCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Generator$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Generator$2.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Generator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GestureGenerator$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GestureGenerator$2.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GestureGenerator$3.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GestureGenerator$4.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GestureGenerator$5.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GestureGenerator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GesturePositionEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GestureProgressEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\GestureRecognizedEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\HandleWrapper.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\HandsGenerator$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\HandsGenerator$2.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\HandsGenerator$3.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\HandsGenerator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\HandTouchingFOVEdgeCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\HandTouchingFOVEdgeCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ImageGenerator$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ImageGenerator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ImageMap.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ImageMetaData.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\InactiveHandEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\IObservable.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\IObserver.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\IRGenerator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\IRMap.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\IRMetaData.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\IStateChangedObservable.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\License.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\LockHandle.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Log$Severity.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Log.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Map.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\MapGenerator$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\MapGenerator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\MapMetaData.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\MapOutputMode.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\MirrorCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\MirrorCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\NativeMethods.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\NodeCreatedEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\NodeDestroyedEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\NodeInfo.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\NodeInfoList$NodeInfoListIterator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\NodeInfoList.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\NodeType.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\NodeWrapper.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ObjectWrapper.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Observable.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\OutArg.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\OutputMetaData.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PixelFormat.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Plane3D.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Player$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Player.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PlayerSeekOrigin.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Point3D.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PoseDetectionCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PoseDetectionCapability$2.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PoseDetectionCapability$3.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PoseDetectionCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PoseDetectionEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PoseDetectionInProgressEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PoseDetectionState.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PoseDetectionStatus.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\PowerLineFrequency.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ProductionNode.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ProductionNodeDescription.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Query.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Recorder.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\RecordMedium.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Resolution.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SceneAnalyzer.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SceneMap.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SceneMetaData.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ScriptNode.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\ShortMap.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonCapability$2.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonCapability$3.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonCapability$4.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonJoint.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonJointOrientation.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonJointPosition.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonJointTransformation.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonPoseProcessingMode.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\SkeletonProfile.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\StateChangedObservable.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\StatusException.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\UserEventArgs.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\UserGenerator$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\UserGenerator$2.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\UserGenerator$3.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\UserGenerator$4.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\UserGenerator.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\UserPositionCapability$1.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\UserPositionCapability.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\Version.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\WaveOutputMode.class
    The system cannot find the path specified.
!   C:\Program Files (x86)\OpenNI\Bin\org.OpenNI.jar: Cannot create org\OpenNI\WrapperUtils.class
    The system cannot find the path specified.

Did i do something wrong?

---

### Post by ofnuts on 2014-02-12
Are you on Windows or on Linux? I didn't tell you to uncompress it, but to chech the contents (WinRar will display the contents, if asked politely).

This said, this JAR only contains some OpenNI framework/library.

Start by locating real javac executable (your "javac" is likely the start of a chain of links to the real one.

Also search your system for a "rt.jar" (looks like Java runtimes (open, Sun/Oracle, or IBM) all contain one), normally not very far from your real javac.

---

