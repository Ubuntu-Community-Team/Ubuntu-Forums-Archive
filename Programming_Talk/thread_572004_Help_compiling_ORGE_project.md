---
title: "Help compiling ORGE project"
date: 2007-10-09
forum: Programming Talk
---

### Post by kthakore on 2007-10-09
I recently installed ORGE SDK from source on Feisty with the following commands

```

./configure --enable-openexr --disable-freeimage
make 
sudo make install

```

here is the make file for my project 
```
 
DEFINES =
LIBS = OGRE audiere
CXX = g++
CXXFLAGS = $(shell pkg-config --cflags $(LIBS)) $(DEFINES)
LD = g++
LDFLAGS = $(shell pkg-config --libs $(LIBS))

all:
	$(CXX) $(CXXFLAGS) $(LDFLAGS) -o SampleApp sample.cpp

clean:
	rm -f SampleApp

```

however it will not compile giving me errors indicating that the Ogre.h file is not read. What am I doing wrong?

---

### Post by kthakore on 2007-10-10
Ok guess no one uses OGRE. Well has anyone have success with crystalspace or any of the other 3d game engines?

---

### Post by Compyx on 2007-10-11
> **kthakore said:**
> 
however it will not compile giving me errors indicating that the Ogre.h file is not read. What am I doing wrong?

You're unlikely to get any help if you don't show the error messages and the offending code. All I can say at this point is that the error is probably at line 42.

---

### Post by Auria on 2007-10-11
If you get no answer here, you should also try the ogre forums. There, everyone uses Ogre so you'll have much better chances of gettings answers

---

### Post by kthakore on 2007-10-11
I took out line 43 and tried again
here is the code

```

/*
Magic of Stonehenge demo v1.0

Programming: 
Arsen Gnatkivsky "Troglodit"
e-mail: trogl@inbox.ru

used engines:

OGRE    : http://www.ogre3d.org
audiere : http://audiere.sourceforge.net/
*/

#include "ExampleApplication.h"
#include <audiere.h>

ParticleSystem *pThrusters;
AnimationState* mAnimState;
SceneNode* camNode;
Overlay* mBlackOverlay;

audiere::AudioDevicePtr device(audiere::OpenDevice());
audiere::OutputStreamPtr stream(audiere::OpenSound(device, "music.wav", false));

std::ofstream posLog("position.log");

class SkyBoxFrameListener : public ExampleFrameListener
{
private:
        static float fDefDim;
        static float fDefVel;

public:
        SkyBoxFrameListener(RenderWindow* win, Camera* cam) : ExampleFrameListener( win, cam )
        {
                showDebugOverlay(false);
        }

        bool frameStarted( const FrameEvent& evt )
        {

                mAnimState->addTime(evt.timeSinceLastFrame);

                bool bOK = ExampleFrameListener::frameStarted( evt );

                static Real tim=0;
                tim+=evt.timeSinceLastEvent;
                static bool nothold=true;

// This peace op code you need when you capture the camera motion
// it will generate c++ code for keyframes in separate file
/*              if( mInputDevice->isKeyDown( KC_SPACE ) )
                {
                        if (nothold==true){

                                nothold=false;
                                mWindow->setDebugText("!!!!!");

                                Quaternion ori=mCamera->getOrientation();
                                Vector3 pos=mCamera->getPosition();

                                posLog << "key = track->createKeyFrame(animDelay*"<<tim<<"+timOffset);\n";
                                posLog <<"key->setTranslate(Vector3("<< pos.x << "," << pos.y << "," << pos.z << "));\n";
                                posLog <<"key->setRotation(Quaternion("<< ori.w << "," << ori.x << "," << ori.y << "," << ori.z << "));\n";
                        }
                } else {
                        nothold=true;
                }
*/


                static int nohide=3;
                static bool isTest=true;
                if (isTest){

                        if (nohide<1) {
                                mBlackOverlay->hide();
                                isTest=false;
                        }
                        else  nohide--;
                }
                return bOK;
        }
};

float SkyBoxFrameListener::fDefDim = 25.0f;
float SkyBoxFrameListener::fDefVel = 50.0f;

class SkyBoxApplication : public ExampleApplication
{
public:
        SkyBoxApplication() {}

protected:
        virtual void createFrameListener(void)
        {
                mFrameListener= new SkyBoxFrameListener(mWindow, mCamera);
                mRoot->addFrameListener(mFrameListener);
        }

        // Just override the mandatory create scene method
        void createScene(void)
        {

                stream->setRepeat(true);
                stream->setVolume(0.5f); // 50% volume
                stream->play();


                // Set ambient light
                mSceneMgr->setAmbientLight(ColourValue(0.5, 0.5, 0.5));

                // Create a light
                Light* l = mSceneMgr->createLight("MainLight");

                l->setPosition(20,80,50);


                //------------------------------------------
                Entity *ground = mSceneMgr->createEntity( "ground", "Plane01.mesh" );
                Entity *s1 = mSceneMgr->createEntity( "s1", "s1.mesh" );
                Entity *s2 = mSceneMgr->createEntity( "s2", "s2.mesh" );
                Entity *s3 = mSceneMgr->createEntity( "s3", "s3.mesh" );
                Entity *s4 = mSceneMgr->createEntity( "s4", "s4.mesh" );
                Entity *s5 = mSceneMgr->createEntity( "s5", "s5.mesh" );
                Entity *s6 = mSceneMgr->createEntity( "s6", "s6.mesh" );
                Entity *s7 = mSceneMgr->createEntity( "s7", "s7.mesh" );
                Entity *s8 = mSceneMgr->createEntity( "s8", "s8.mesh" );
                Entity *s9 = mSceneMgr->createEntity( "s9", "s9.mesh" );
                Entity *s10 = mSceneMgr->createEntity( "s10", "s10.mesh" );
                Entity *s11 = mSceneMgr->createEntity( "s11", "s11.mesh" );
                Entity *s12 = mSceneMgr->createEntity( "s12", "s12.mesh" );
                Entity *s13 = mSceneMgr->createEntity( "s13", "s13.mesh" );
                Entity *s14 = mSceneMgr->createEntity( "s14", "s14.mesh" );
                Entity *s15 = mSceneMgr->createEntity( "s15", "s15.mesh" );

                mSceneMgr->getRootSceneNode()->attachObject(ground);
                mSceneMgr->getRootSceneNode()->attachObject(s1);
                mSceneMgr->getRootSceneNode()->attachObject(s2);
                mSceneMgr->getRootSceneNode()->attachObject(s3);
                mSceneMgr->getRootSceneNode()->attachObject(s4);
                mSceneMgr->getRootSceneNode()->attachObject(s5);
                mSceneMgr->getRootSceneNode()->attachObject(s6);
                mSceneMgr->getRootSceneNode()->attachObject(s7);
                mSceneMgr->getRootSceneNode()->attachObject(s8);
                mSceneMgr->getRootSceneNode()->attachObject(s9);
                mSceneMgr->getRootSceneNode()->attachObject(s10);
                mSceneMgr->getRootSceneNode()->attachObject(s11);
                mSceneMgr->getRootSceneNode()->attachObject(s12);
                mSceneMgr->getRootSceneNode()->attachObject(s13);
                mSceneMgr->getRootSceneNode()->attachObject(s14);
                mSceneMgr->getRootSceneNode()->attachObject(s15);

                Entity *cast1 = mSceneMgr->createEntity( "cast1", "cast1.mesh" );
                mSceneMgr->getRootSceneNode()->attachObject(cast1);

                Entity *pilon = mSceneMgr->createEntity( "pilon", "pilon.mesh" );
                mSceneMgr->getRootSceneNode()->attachObject(pilon);


                ParticleSystem* pSys2 = ParticleSystemManager::getSingleton().createSystem("fountain1", "PEExamples/stoneh2");
                mSceneMgr->getRootSceneNode()->attachObject(pSys2);


                ParticleSystem* pSys3 = ParticleSystemManager::getSingleton().createSystem("fountain2", "PEExamples/stoneh2_small");
                ParticleSystem* pSys4 = ParticleSystemManager::getSingleton().createSystem("fountain3", "PEExamples/stoneh2_small");
                ParticleSystem* pSys5 = ParticleSystemManager::getSingleton().createSystem("fountain4", "PEExamples/stoneh2_small");
                SceneNode* spout_node1=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                SceneNode* spout_node2=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                SceneNode* spout_node3=mSceneMgr->getRootSceneNode()->createChildSceneNode();


                spout_node1->attachObject(pSys3);
                spout_node2->attachObject(pSys4);
                spout_node3->attachObject(pSys5);

                Real max2ogre=0.025;
                Vector3 triSpoutPos1=Vector3(-0.084/max2ogre,0.354/max2ogre,-7.047/max2ogre);
                Vector3 triSpoutPos2=Vector3(5.872/max2ogre,0.354/max2ogre,3.461/max2ogre);
                Vector3 triSpoutPos3=Vector3(-5.787/max2ogre,0.354/max2ogre,3.351/max2ogre);


                spout_node1->setPosition(triSpoutPos1);
                spout_node2->setPosition(triSpoutPos2);
                spout_node3->setPosition(triSpoutPos3);





                Entity *cast3 = mSceneMgr->createEntity( "cast3", "cast1.mesh" );
                SceneNode* cast3_node=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                cast3_node->attachObject(cast3);
                cast3_node->setScale(5,1,5);
                cast3_node->setPosition(0,100,0);
                cast3->setMaterialName("cast3");

                Entity *cast4 = mSceneMgr->createEntity( "cast4", "cast1.mesh" );
                SceneNode* cast4_node=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                cast4_node->attachObject(cast4);
                cast4_node->setScale(2,1,2);
                cast4_node->setPosition(0,200,0);
                cast4->setMaterialName("cast4");



                Entity *castTri1 = mSceneMgr->createEntity( "castTri1", "cast1.mesh" );
                SceneNode* castTriNode1=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                castTriNode1->attachObject(castTri1);
                castTriNode1->setScale(0.5,0.1,0.5);
                castTriNode1->setPosition(triSpoutPos1-Vector3(0,-10,0));
                castTri1->setMaterialName("castTri");



                Entity *castSun2 = mSceneMgr->createEntity( "castSun2", "cast1.mesh" );
                SceneNode* castSunNode2=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                castSunNode2->attachObject(castSun2);
                castSunNode2->setScale(1.5,0.1,1.5);
                //castSunNode1->setPosition(triSpoutPos1-Vector3(0,-10,0));
                castSunNode2->setPosition(0,10,0);
                castSun2->setMaterialName("castsun1");


                for (int sc=1;sc<20;sc++) {

                        Entity *castSun1 = mSceneMgr->createEntity( "castSun1"+StringConverter::toString(sc), "cast1.mesh" );
                        SceneNode* castSunNode1=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                        castSunNode1->attachObject(castSun1);
                        castSunNode1->setScale(2.5-sc*0.05,0.1,2.5-sc*0.05);
                        //castSunNode1->setPosition(triSpoutPos1-Vector3(0,-10,0));
                        castSunNode1->setPosition(0,40+sc*10,0);
                        castSunNode1->yaw(Radian(0.5));
                        castSunNode1->pitch(Radian(rand()%5));
                        castSunNode1->roll(Radian(rand()%5));
                        castSun1->setMaterialName("castsun");
                };

                Entity *castTri2 = mSceneMgr->createEntity( "castTri2", "cast1.mesh" );
                SceneNode* castTriNode2=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                castTriNode2->attachObject(castTri2);
                castTriNode2->setScale(0.5,0.1,0.5);
                castTriNode2->setPosition(triSpoutPos2-Vector3(0,-10,0));
                castTriNode2->yaw(Radian(-90.0));
                castTri2->setMaterialName("castTri");

                Entity *castTri3 = mSceneMgr->createEntity( "castTri3", "cast1.mesh" );
                SceneNode* castTriNode3=mSceneMgr->getRootSceneNode()->createChildSceneNode();
                castTriNode3->attachObject(castTri3);
                castTriNode3->setScale(0.5,0.1,0.5);
                castTriNode3->setPosition(triSpoutPos3-Vector3(0,-10,0));
                castTriNode3->yaw(Radian(90.0));
                castTri3->setMaterialName("castTri");


                Entity *gorizont = mSceneMgr->createEntity( "gorizont", "gorizont.mesh" );
                mSceneMgr->getRootSceneNode()->attachObject(gorizont);
                Entity *barier = mSceneMgr->createEntity( "barier", "barier.mesh" );
                mSceneMgr->getRootSceneNode()->attachObject(barier);

                //-----------------------------------------
                SceneNode* lookNode= mSceneMgr->getRootSceneNode()->createChildSceneNode();
                lookNode->setPosition(0,200,0);

                camNode = mSceneMgr->getRootSceneNode()->createChildSceneNode();
                camNode->attachObject(mCamera);
                mCamera->setPosition(0,0,0);

                camNode->setPosition(-244.852,392.682,-357.77);
                camNode->setOrientation(Quaternion(0.345054,-0.0821347,0.909552,0.216516));

                camNode->needUpdate();

                // set up spline animation of node
                Animation* anim = mSceneMgr->createAnimation("CameraTrack",319.382-28.307);// 319.382-28.5128
                // Spline it for nice curves
                anim->setInterpolationMode(Animation::IM_SPLINE);

                //anim->setInterpolationMode(Animation::IM_LINEAR);
                // Create a track to animate the camera's node
                AnimationTrack* track = anim->createTrack(0, camNode);
                // Setup keyframes
                KeyFrame* key;
                key = track->createKeyFrame(0); // startposition

                unsigned fr=0;

                Real animDelay=1;
                Real timOffset=-28.8307*animDelay;


                key = track->createKeyFrame(animDelay*28.8307+timOffset);
                key->setTranslate(Vector3(-244.852,392.682,-357.77));
                key->setRotation(Quaternion(0.345054,-0.0821347,0.909552,0.216516));
                key = track->createKeyFrame(animDelay*35.2817+timOffset);
                key->setTranslate(Vector3(-393.737,294.394,-113.343));
                key->setRotation(Quaternion(-0.306394,0.0508652,0.937698,0.155653));
                key = track->createKeyFrame(animDelay*40.6439+timOffset);
                key->setTranslate(Vector3(-422.293,349.852,173.018));
                key->setRotation(Quaternion(-0.800221,0.201077,0.547927,0.137671));
                key = track->createKeyFrame(animDelay*49.6474+timOffset);
                key->setTranslate(Vector3(-79.646,349.852,560.048));
                key->setRotation(Quaternion(-0.896801,0.294858,0.313268,0.102994));
                key = track->createKeyFrame(animDelay*58.5187+timOffset);
                key->setTranslate(Vector3(501.429,267.73,432.065));
                key->setRotation(Quaternion(-0.993273,0.115458,-0.000865597,-0.000100481));
                key = track->createKeyFrame(animDelay*67.743+timOffset);
                key->setTranslate(Vector3(640.836,323.694,-73.3012));
                key->setRotation(Quaternion(-0.605509,0.0523376,-0.79111,-0.0683883));
                key = track->createKeyFrame(animDelay*82.8461+timOffset);
                key->setTranslate(Vector3(169.581,523.395,-738.473));
                key->setRotation(Quaternion(-0.153773,0.0488329,-0.940583,-0.298618));
                key = track->createKeyFrame(animDelay*94.9738+timOffset);
                key->setTranslate(Vector3(-544.202,335.46,-620.324));
                key->setRotation(Quaternion(-0.0808456,0.0166631,-0.976055,-0.200973));
                key = track->createKeyFrame(animDelay*114.848+timOffset);
                key->setTranslate(Vector3(-1279.63,1060.58,186.159));
                key->setRotation(Quaternion(0.734783,-0.290591,-0.569856,-0.22537));
                key = track->createKeyFrame(animDelay*129.583+timOffset);
                key->setTranslate(Vector3(-892.411,1131.63,999.012));
                key->setRotation(Quaternion(0.837642,-0.232815,-0.47594,-0.132303));
                key = track->createKeyFrame(animDelay*141.035+timOffset);
                key->setTranslate(Vector3(-404.345,716.693,1474.86));
                key->setRotation(Quaternion(0.905332,-0.191741,-0.370559,-0.0785072));
                key = track->createKeyFrame(animDelay*154.269+timOffset);
                key->setTranslate(Vector3(528.32,321.039,1093.36));
                key->setRotation(Quaternion(0.949058,-0.24763,0.188184,0.0490821));
                key = track->createKeyFrame(animDelay*167.148+timOffset);
                key->setTranslate(Vector3(245.522,66.4289,417.204));
                key->setRotation(Quaternion(0.969895,-0.00327889,0.243174,0.000821591));

                key = track->createKeyFrame(animDelay*180+timOffset);
                key->setTranslate(Vector3(74.5456,161.762,229.612));
                key->setRotation(Quaternion(0.919624,-0.37099,0.119602,0.048247));
                key = track->createKeyFrame(animDelay*200+timOffset);
                key->setTranslate(Vector3(99.7407,953.843,310.485));
                key->setRotation(Quaternion(0.815697,-0.560923,0.116455,0.0800779));

                key = track->createKeyFrame(animDelay*213.003+timOffset);
                key->setTranslate(Vector3(740.743,158.305,165.596));
                key->setRotation(Quaternion(0.461686,-0.0305725,0.884463,0.0582964));
                key = track->createKeyFrame(animDelay*231.324+timOffset);
                key->setTranslate(Vector3(1889.01,281.073,89.9274));
                key->setRotation(Quaternion(0.723468,0.00313488,0.690157,-0.00313797));
                key = track->createKeyFrame(animDelay*249.487+timOffset);
                key->setTranslate(Vector3(2872.93,118.85,-472.164));
                key->setRotation(Quaternion(0.657661,0.0386955,0.750839,-0.0443189));
                key = track->createKeyFrame(animDelay*264.965+timOffset);
                key->setTranslate(Vector3(2613.98,169.808,-1362.87));
                key->setRotation(Quaternion(0.515329,0.0279485,0.855113,-0.0465596));
                key = track->createKeyFrame(animDelay*278.284+timOffset);
                key->setTranslate(Vector3(2000.71,209.627,-1909.93));
                key->setRotation(Quaternion(0.39415,0.0271869,0.916301,-0.0634344));
                key = track->createKeyFrame(animDelay*292.262+timOffset);
                key->setTranslate(Vector3(844.269,282.555,-1766.07));
                key->setRotation(Quaternion(0.227154,0.00503583,0.973453,-0.0220159));
                key = track->createKeyFrame(animDelay*308.494+timOffset);
                key->setTranslate(Vector3(34.4144,291.87,-1023.65));
                key->setRotation(Quaternion(0.0827656,-0.00208207,0.996139,0.023802));

                key = track->createKeyFrame(animDelay*319.382+timOffset);
                key->setTranslate(Vector3(-244.852,392.682,-357.77));
                key->setRotation(Quaternion(0.345054,-0.0821347,0.909552,0.216516));



                // Create a new animation state to track this
                mAnimState = mSceneMgr->createAnimationState("CameraTrack");
                mAnimState->setEnabled(true);



                mBlackOverlay = OverlayManager::getSingleton().getByName("BLACK");
                mBlackOverlay->show();





        }

};


```

this is the error I get

```
make
Package audiere was not found in the pkg-config search path.
Perhaps you should add the directory containing `audiere.pc'
to the PKG_CONFIG_PATH environment variable
No package 'audiere' found
Package audiere was not found in the pkg-config search path.
Perhaps you should add the directory containing `audiere.pc'
to the PKG_CONFIG_PATH environment variable
No package 'audiere' found
g++    -o SampleApp sample.cpp
In file included from sample.cpp:14:
ExampleApplication.h:24:18: error: Ogre.h: No such file or directory
ExampleApplication.h:25:28: error: OgreConfigFile.h: No such file or directory
In file included from ExampleApplication.h:26,
                 from sample.cpp:14:
ExampleFrameListener.h:39:33: error: OgreStringConverter.h: No such file or directory
ExampleFrameListener.h:40:27: error: OgreException.h: No such file or directory
In file included from sample.cpp:14:
ExampleApplication.h:29:43: error: CoreFoundation/CoreFoundation.h: No such file or directory
ExampleFrameListener.h:47: error: ‘Ogre’ is not a namespace-name
ExampleFrameListener.h:47: error: expected namespace-name before ‘;’ token
ExampleFrameListener.h:49: error: expected class-name before ‘,’ token
ExampleFrameListener.h:50: error: expected class-name before ‘{’ token
ExampleFrameListener.h:90: error: expected `)' before ‘*’ token
ExampleFrameListener.h:132: error: ‘RenderWindow’ has not been declared
ExampleFrameListener.h:144: error: ‘RenderWindow’ has not been declared
ExampleFrameListener.h:168: error: expected ‘,’ or ‘...’ before ‘&’ token
ExampleFrameListener.h:168: error: ISO C++ forbids declaration of ‘FrameEvent’ with no type
ExampleFrameListener.h:269: error: expected ‘,’ or ‘...’ before ‘&’ token
ExampleFrameListener.h:269: error: ISO C++ forbids declaration of ‘FrameEvent’ with no type
ExampleFrameListener.h:312: error: expected ‘,’ or ‘...’ before ‘&’ token
ExampleFrameListener.h:312: error: ISO C++ forbids declaration of ‘FrameEvent’ with no type
ExampleFrameListener.h:365: error: expected ‘,’ or ‘...’ before ‘&’ token
ExampleFrameListener.h:365: error: ISO C++ forbids declaration of ‘FrameEvent’ with no type
ExampleFrameListener.h:372: error: ISO C++ forbids declaration of ‘Camera’ with no type
ExampleFrameListener.h:372: error: expected ‘;’ before ‘*’ token
ExampleFrameListener.h:374: error: ‘Vector3’ does not name a type
ExampleFrameListener.h:375: error: ISO C++ forbids declaration of ‘RenderWindow’ with no type
ExampleFrameListener.h:375: error: expected ‘;’ before ‘*’ token
ExampleFrameListener.h:382: error: ‘Degree’ does not name a type
ExampleFrameListener.h:384: error: ‘Real’ does not name a type
ExampleFrameListener.h:385: error: ‘Radian’ does not name a type
ExampleFrameListener.h:386: error: ‘TextureFilterOptions’ does not name a type
ExampleFrameListener.h:390: error: ‘Real’ does not name a type
ExampleFrameListener.h:391: error: ‘Degree’ does not name a type
ExampleFrameListener.h:392: error: ISO C++ forbids declaration of ‘Overlay’ with no type
ExampleFrameListener.h:392: error: expected ‘;’ before ‘*’ token
ExampleFrameListener.h: In member function ‘void ExampleFrameListener::updateStats()’:
ExampleFrameListener.h:54: error: ‘String’ does not name a type
ExampleFrameListener.h:55: error: ‘String’ does not name a type
ExampleFrameListener.h:56: error: ‘String’ does not name a type
ExampleFrameListener.h:57: error: ‘String’ does not name a type
ExampleFrameListener.h:58: error: ‘String’ does not name a type
ExampleFrameListener.h:59: error: ‘String’ does not name a type
ExampleFrameListener.h:63: error: ‘OverlayElement’ was not declared in this scope
ExampleFrameListener.h:63: error: ‘guiAvg’ was not declared in this scope
ExampleFrameListener.h:63: error: ‘OverlayManager’ has not been declared
ExampleFrameListener.h:64: error: ‘guiCurr’ was not declared in this scope
ExampleFrameListener.h:64: error: ‘OverlayManager’ has not been declared
ExampleFrameListener.h:65: error: ‘guiBest’ was not declared in this scope
ExampleFrameListener.h:65: error: ‘OverlayManager’ has not been declared
ExampleFrameListener.h:66: error: ‘guiWorst’ was not declared in this scope
ExampleFrameListener.h:66: error: ‘OverlayManager’ has not been declared
ExampleFrameListener.h:68: error: ‘RenderTarget’ has not been declared
ExampleFrameListener.h:68: error: expected initializer before ‘&’ token
ExampleFrameListener.h:69: error: ‘avgFps’ was not declared in this scope
ExampleFrameListener.h:69: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:69: error: ‘stats’ was not declared in this scope
ExampleFrameListener.h:70: error: ‘currFps’ was not declared in this scope
ExampleFrameListener.h:70: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:71: error: ‘bestFps’ was not declared in this scope
ExampleFrameListener.h:71: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:72: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:73: error: ‘worstFps’ was not declared in this scope
ExampleFrameListener.h:73: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:74: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:76: error: ‘guiTris’ was not declared in this scope
ExampleFrameListener.h:76: error: ‘OverlayManager’ has not been declared
ExampleFrameListener.h:77: error: ‘tris’ was not declared in this scope
ExampleFrameListener.h:77: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:79: error: ‘guiBatches’ was not declared in this scope
ExampleFrameListener.h:79: error: ‘OverlayManager’ has not been declared
ExampleFrameListener.h:80: error: ‘batches’ was not declared in this scope
ExampleFrameListener.h:80: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:82: error: ‘guiDbg’ was not declared in this scope
ExampleFrameListener.h:82: error: ‘OverlayManager’ has not been declared
ExampleFrameListener.h: In member function ‘virtual void ExampleFrameListener::windowResized(int*)’:
ExampleFrameListener.h:136: error: request for member ‘getMetrics’ in ‘* rw’, which is of non-class type ‘int’
ExampleFrameListener.h: In member function ‘virtual void ExampleFrameListener::windowClosed(int*)’:
ExampleFrameListener.h:147: error: ‘mWindow’ was not declared in this scope
ExampleFrameListener.h: In destructor ‘virtual ExampleFrameListener::~ExampleFrameListener()’:
ExampleFrameListener.h:164: error: ‘WindowEventUtilities’ has not been declared
ExampleFrameListener.h:164: error: ‘mWindow’ was not declared in this scope
ExampleFrameListener.h: In member function ‘virtual bool ExampleFrameListener::processUnbufferedKeyInput(int)’:
ExampleFrameListener.h:173: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h:176: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h:179: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h:182: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h:185: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h:188: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h:191: error: ‘mCamera’ was not declared in this scope
ExampleFrameListener.h:191: error: ‘mRotScale’ was not declared in this scope
ExampleFrameListener.h:194: error: ‘mCamera’ was not declared in this scope
ExampleFrameListener.h:194: error: ‘mRotScale’ was not declared in this scope
ExampleFrameListener.h:199: error: ‘mTimeUntilNextToggle’ was not declared in this scope
ExampleFrameListener.h:206: error: ‘mTimeUntilNextToggle’ was not declared in this scope
ExampleFrameListener.h:208: error: ‘mFiltering’ was not declared in this scope
ExampleFrameListener.h:210: error: ‘TFO_BILINEAR’ was not declared in this scope
ExampleFrameListener.h:211: error: ‘TFO_TRILINEAR’ was not declared in this scope
ExampleFrameListener.h:214: error: ‘TFO_TRILINEAR’ cannot appear in a constant-expression
ExampleFrameListener.h:215: error: ‘TFO_ANISOTROPIC’ was not declared in this scope
ExampleFrameListener.h:218: error: ‘TFO_ANISOTROPIC’ cannot appear in a constant-expression
ExampleFrameListener.h:224: error: ‘MaterialManager’ has not been declared
ExampleFrameListener.h:224: error: ‘mFiltering’ was not declared in this scope
ExampleFrameListener.h:225: error: ‘MaterialManager’ has not been declared
ExampleFrameListener.h:231: error: ‘mTimeUntilNextToggle’ was not declared in this scope
ExampleFrameListener.h:233: error: aggregate ‘std::ostringstream ss’ has incomplete type and cannot be defined
ExampleFrameListener.h:235: error: ‘mWindow’ was not declared in this scope
ExampleFrameListener.h:240: error: ‘mTimeUntilNextToggle’ was not declared in this scope
ExampleFrameListener.h:244: error: ‘mCamera’ was not declared in this scope
ExampleFrameListener.h:244: error: ‘PM_SOLID’ was not declared in this scope
ExampleFrameListener.h:245: error: ‘PM_WIREFRAME’ was not declared in this scope
ExampleFrameListener.h:246: error: ‘PM_POINTS’ was not declared in this scope
ExampleFrameListener.h:252: error: ‘mTimeUntilNextToggle’ was not declared in this scope
ExampleFrameListener.h:262: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h:262: error: ‘mCamera’ was not declared in this scope
ExampleFrameListener.h:263: error: ‘StringConverter’ has not been declared
ExampleFrameListener.h: In member function ‘bool ExampleFrameListener::processUnbufferedMouseInput(int)’:
ExampleFrameListener.h:278: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h:283: error: ‘mRotX’ was not declared in this scope
ExampleFrameListener.h:283: error: ‘Degree’ was not declared in this scope
ExampleFrameListener.h:284: error: ‘mRotY’ was not declared in this scope
ExampleFrameListener.h: In member function ‘void ExampleFrameListener::moveCamera()’:
ExampleFrameListener.h:295: error: ‘mCamera’ was not declared in this scope
ExampleFrameListener.h:295: error: ‘mRotX’ was not declared in this scope
ExampleFrameListener.h:296: error: ‘mRotY’ was not declared in this scope
ExampleFrameListener.h:297: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h: In member function ‘void ExampleFrameListener::showDebugOverlay(bool)’:
ExampleFrameListener.h:302: error: ‘mDebugOverlay’ was not declared in this scope
ExampleFrameListener.h: In member function ‘bool ExampleFrameListener::frameStarted(int)’:
ExampleFrameListener.h:316: error: ‘mWindow’ was not declared in this scope
ExampleFrameListener.h:329: error: ‘mTimeUntilNextToggle’ was not declared in this scope
ExampleFrameListener.h:330: error: ‘evt’ was not declared in this scope
ExampleFrameListener.h:333: error: ‘evt’ was not declared in this scope
ExampleFrameListener.h:336: error: ‘mRotScale’ was not declared in this scope
ExampleFrameListener.h:342: error: ‘mMoveSpeed’ was not declared in this scope
ExampleFrameListener.h:344: error: ‘mRotScale’ was not declared in this scope
ExampleFrameListener.h:344: error: ‘mRotateSpeed’ was not declared in this scope
ExampleFrameListener.h:346: error: ‘mRotX’ was not declared in this scope
ExampleFrameListener.h:347: error: ‘mRotY’ was not declared in this scope
ExampleFrameListener.h:348: error: ‘mTranslateVector’ was not declared in this scope
ExampleFrameListener.h:348: error: ‘Ogre’ has not been declared
ExampleFrameListener.h:353: error: ‘evt’ was not declared in this scope
ExampleFrameListener.h:356: error: ‘evt’ was not declared in this scope
ExampleApplication.h: In function ‘std::string macBundlePath()’:
ExampleApplication.h:37: error: ‘CFBundleRef’ was not declared in this scope
ExampleApplication.h:37: error: expected `;' before ‘mainBundle’
ExampleApplication.h:38: error: ‘mainBundle’ was not declared in this scope
ExampleApplication.h:38: error: ‘assert’ was not declared in this scope
ExampleApplication.h:40: error: ‘CFURLRef’ was not declared in this scope
ExampleApplication.h:40: error: expected `;' before ‘mainBundleURL’
ExampleApplication.h:41: error: ‘mainBundleURL’ was not declared in this scope
ExampleApplication.h:43: error: ‘CFStringRef’ was not declared in this scope
ExampleApplication.h:43: error: expected `;' before ‘cfStringRef’
ExampleApplication.h:44: error: ‘cfStringRef’ was not declared in this scope
ExampleApplication.h:46: error: ‘kCFStringEncodingASCII’ was not declared in this scope
ExampleApplication.h:46: error: ‘CFStringGetCString’ was not declared in this scope
ExampleApplication.h:48: error: ‘CFRelease’ was not declared in this scope
ExampleApplication.h: At global scope:
ExampleApplication.h:55: error: ‘Ogre’ is not a namespace-name
ExampleApplication.h:55: error: expected namespace-name before ‘;’ token
ExampleApplication.h:99: error: ISO C++ forbids declaration of ‘Root’ with no type
ExampleApplication.h:99: error: expected ‘;’ before ‘*’ token
ExampleApplication.h:100: error: ISO C++ forbids declaration of ‘Camera’ with no type
ExampleApplication.h:100: error: expected ‘;’ before ‘*’ token
ExampleApplication.h:101: error: ISO C++ forbids declaration of ‘SceneManager’ with no type
ExampleApplication.h:101: error: expected ‘;’ before ‘*’ token
ExampleApplication.h:103: error: ISO C++ forbids declaration of ‘RenderWindow’ with no type
ExampleApplication.h:103: error: expected ‘;’ before ‘*’ token
ExampleApplication.h:104: error: ‘Ogre’ has not been declared
ExampleApplication.h:104: error: ISO C++ forbids declaration of ‘String’ with no type
ExampleApplication.h:104: error: expected ‘;’ before ‘mResourcePath’
ExampleApplication.h: In constructor ‘ExampleApplication::ExampleApplication()’:
ExampleApplication.h:67: error: ‘mRoot’ was not declared in this scope
ExampleApplication.h:72: error: ‘mResourcePath’ was not declared in this scope
ExampleApplication.h: In destructor ‘virtual ExampleApplication::~ExampleApplication()’:
ExampleApplication.h:82: error: ‘mRoot’ was not declared in this scope
ExampleApplication.h:83: error: type ‘<type error>’ argument given to ‘delete’, expected pointer
ExampleApplication.h: In member function ‘virtual void ExampleApplication::go()’:
ExampleApplication.h:92: error: ‘mRoot’ was not declared in this scope
ExampleApplication.h: In member function ‘virtual bool ExampleApplication::setup()’:
ExampleApplication.h:111: error: ‘String’ was not declared in this scope
ExampleApplication.h:111: error: expected `;' before ‘pluginsPath’
ExampleApplication.h:114: error: ‘pluginsPath’ was not declared in this scope
ExampleApplication.h:114: error: ‘mResourcePath’ was not declared in this scope
ExampleApplication.h:117: error: ‘mRoot’ was not declared in this scope
ExampleApplication.h:117: error: expected type-specifier before ‘Root’
ExampleApplication.h:117: error: expected `;' before ‘Root’
ExampleApplication.h:130: error: ‘TextureManager’ has not been declared
ExampleApplication.h: In member function ‘virtual bool ExampleApplication::configure()’:
ExampleApplication.h:151: error: ‘mRoot’ was not declared in this scope
ExampleApplication.h:155: error: ‘mWindow’ was not declared in this scope
ExampleApplication.h: In member function ‘virtual void ExampleApplication::chooseSceneManager()’:
ExampleApplication.h:167: error: ‘mSceneMgr’ was not declared in this scope
ExampleApplication.h:167: error: ‘mRoot’ was not declared in this scope
ExampleApplication.h:167: error: ‘ST_GENERIC’ was not declared in this scope
ExampleApplication.h: In member function ‘virtual void ExampleApplication::createCamera()’:
ExampleApplication.h:172: error: ‘mCamera’ was not declared in this scope
ExampleApplication.h:172: error: ‘mSceneMgr’ was not declared in this scope
ExampleApplication.h:175: error: ‘Vector3’ was not declared in this scope
ExampleApplication.h: In member function ‘virtual void ExampleApplication::createFrameListener()’:
ExampleApplication.h:183: error: ‘mWindow’ was not declared in this scope
ExampleApplication.h:183: error: ‘mCamera’ was not declared in this scope
ExampleApplication.h:185: error: ‘mRoot’ was not declared in this scope
ExampleApplication.h: In member function ‘virtual void ExampleApplication::createViewports()’:
ExampleApplication.h:195: error: ‘Viewport’ was not declared in this scope
ExampleApplication.h:195: error: ‘vp’ was not declared in this scope
ExampleApplication.h:195: error: ‘mWindow’ was not declared in this scope
ExampleApplication.h:195: error: ‘mCamera’ was not declared in this scope
ExampleApplication.h:196: error: ‘ColourValue’ was not declared in this scope
ExampleApplication.h:200: error: ‘Real’ was not declared in this scope
ExampleApplication.h: In member function ‘virtual void ExampleApplication::setupResources()’:
ExampleApplication.h:207: error: ‘ConfigFile’ was not declared in this scope
ExampleApplication.h:207: error: expected `;' before ‘cf’
ExampleApplication.h:208: error: ‘cf’ was not declared in this scope
ExampleApplication.h:208: error: ‘mResourcePath’ was not declared in this scope
ExampleApplication.h:211: error: ‘ConfigFile’ is not a class or namespace
ExampleApplication.h:211: error: expected `;' before ‘seci’
ExampleApplication.h:213: error: ‘String’ was not declared in this scope
ExampleApplication.h:213: error: expected `;' before ‘secName’
ExampleApplication.h:214: error: ‘seci’ was not declared in this scope
ExampleApplication.h:216: error: ‘secName’ was not declared in this scope
ExampleApplication.h:217: error: ‘ConfigFile’ is not a class or namespace
ExampleApplication.h:217: error: ‘settings’ was not declared in this scope
ExampleApplication.h:218: error: ‘ConfigFile’ is not a class or namespace
ExampleApplication.h:218: error: expected `;' before ‘i’
ExampleApplication.h:219: error: ‘i’ was not declared in this scope
ExampleApplication.h:221: error: ‘typeName’ was not declared in this scope
ExampleApplication.h:222: error: ‘archName’ was not declared in this scope
ExampleApplication.h:227: error: ‘ResourceGroupManager’ has not been declared
ExampleApplication.h: In member function ‘virtual void ExampleApplication::loadResources()’:
ExampleApplication.h:248: error: ‘ResourceGroupManager’ has not been declared
sample.cpp: At global scope:
sample.cpp:17: error: expected constructor, destructor, or type conversion before ‘*’ token
sample.cpp:18: error: expected constructor, destructor, or type conversion before ‘*’ token
sample.cpp:19: error: expected constructor, destructor, or type conversion before ‘*’ token
sample.cpp:20: error: expected constructor, destructor, or type conversion before ‘*’ token
sample.cpp:25: error: variable ‘std::ofstream posLog’ has initializer but incomplete type
sample.cpp:34: error: expected `)' before ‘*’ token
sample.cpp:39: error: expected ‘,’ or ‘...’ before ‘&’ token
sample.cpp:39: error: ISO C++ forbids declaration of ‘FrameEvent’ with no type
sample.cpp: In member function ‘bool SkyBoxFrameListener::frameStarted(int)’:
sample.cpp:42: error: ‘mAnimState’ was not declared in this scope
sample.cpp:42: error: ‘evt’ was not declared in this scope
sample.cpp:46: error: ‘Real’ does not name a type
sample.cpp:47: error: ‘tim’ was not declared in this scope
sample.cpp:77: error: ‘mBlackOverlay’ was not declared in this scope
sample.cpp: In member function ‘virtual void SkyBoxApplication::createFrameListener()’:
sample.cpp:97: error: ‘mWindow’ was not declared in this scope
sample.cpp:97: error: ‘mCamera’ was not declared in this scope
sample.cpp:98: error: ‘mRoot’ was not declared in this scope
sample.cpp: In member function ‘virtual void SkyBoxApplication::createScene()’:
sample.cpp:111: error: ‘mSceneMgr’ was not declared in this scope
sample.cpp:111: error: ‘ColourValue’ was not declared in this scope
sample.cpp:114: error: ‘Light’ was not declared in this scope
sample.cpp:114: error: ‘l’ was not declared in this scope
sample.cpp:120: error: ‘Entity’ was not declared in this scope
sample.cpp:120: error: ‘ground’ was not declared in this scope
sample.cpp:121: error: ‘s1’ was not declared in this scope
sample.cpp:122: error: ‘s2’ was not declared in this scope
sample.cpp:123: error: ‘s3’ was not declared in this scope
sample.cpp:124: error: ‘s4’ was not declared in this scope
sample.cpp:125: error: ‘s5’ was not declared in this scope
sample.cpp:126: error: ‘s6’ was not declared in this scope
sample.cpp:127: error: ‘s7’ was not declared in this scope
sample.cpp:128: error: ‘s8’ was not declared in this scope
sample.cpp:129: error: ‘s9’ was not declared in this scope
sample.cpp:130: error: ‘s10’ was not declared in this scope
sample.cpp:131: error: ‘s11’ was not declared in this scope
sample.cpp:132: error: ‘s12’ was not declared in this scope
sample.cpp:133: error: ‘s13’ was not declared in this scope
sample.cpp:134: error: ‘s14’ was not declared in this scope
sample.cpp:135: error: ‘s15’ was not declared in this scope
sample.cpp:154: error: ‘cast1’ was not declared in this scope
sample.cpp:157: error: ‘pilon’ was not declared in this scope
sample.cpp:161: error: ‘ParticleSystem’ was not declared in this scope
sample.cpp:161: error: ‘pSys2’ was not declared in this scope
sample.cpp:161: error: ‘ParticleSystemManager’ has not been declared
sample.cpp:165: error: ‘pSys3’ was not declared in this scope
sample.cpp:165: error: ‘ParticleSystemManager’ has not been declared
sample.cpp:166: error: ‘pSys4’ was not declared in this scope
sample.cpp:166: error: ‘ParticleSystemManager’ has not been declared
sample.cpp:167: error: ‘pSys5’ was not declared in this scope
sample.cpp:167: error: ‘ParticleSystemManager’ has not been declared
sample.cpp:168: error: ‘SceneNode’ was not declared in this scope
sample.cpp:168: error: ‘spout_node1’ was not declared in this scope
sample.cpp:169: error: ‘spout_node2’ was not declared in this scope
sample.cpp:170: error: ‘spout_node3’ was not declared in this scope
sample.cpp:177: error: ‘Real’ was not declared in this scope
sample.cpp:177: error: expected `;' before ‘max2ogre’
sample.cpp:178: error: ‘Vector3’ was not declared in this scope
sample.cpp:178: error: expected `;' before ‘triSpoutPos1’
sample.cpp:179: error: expected `;' before ‘triSpoutPos2’
sample.cpp:180: error: expected `;' before ‘triSpoutPos3’
sample.cpp:183: error: ‘triSpoutPos1’ was not declared in this scope
sample.cpp:184: error: ‘triSpoutPos2’ was not declared in this scope
sample.cpp:185: error: ‘triSpoutPos3’ was not declared in this scope
sample.cpp:191: error: ‘cast3’ was not declared in this scope
sample.cpp:192: error: ‘cast3_node’ was not declared in this scope
sample.cpp:198: error: ‘cast4’ was not declared in this scope
sample.cpp:199: error: ‘cast4_node’ was not declared in this scope
sample.cpp:207: error: ‘castTri1’ was not declared in this scope
sample.cpp:208: error: ‘castTriNode1’ was not declared in this scope
sample.cpp:216: error: ‘castSun2’ was not declared in this scope
sample.cpp:217: error: ‘castSunNode2’ was not declared in this scope
sample.cpp:227: error: ‘castSun1’ was not declared in this scope
sample.cpp:227: error: ‘StringConverter’ has not been declared
sample.cpp:228: error: ‘castSunNode1’ was not declared in this scope
sample.cpp:233: error: ‘Radian’ was not declared in this scope
sample.cpp:239: error: ‘castTri2’ was not declared in this scope
sample.cpp:240: error: ‘castTriNode2’ was not declared in this scope
sample.cpp:244: error: ‘Radian’ was not declared in this scope
sample.cpp:247: error: ‘castTri3’ was not declared in this scope
sample.cpp:248: error: ‘castTriNode3’ was not declared in this scope
sample.cpp:256: error: ‘gorizont’ was not declared in this scope
sample.cpp:258: error: ‘barier’ was not declared in this scope
sample.cpp:262: error: ‘lookNode’ was not declared in this scope
sample.cpp:265: error: ‘camNode’ was not declared in this scope
sample.cpp:266: error: ‘mCamera’ was not declared in this scope
sample.cpp:270: error: ‘Quaternion’ was not declared in this scope
sample.cpp:275: error: ‘Animation’ was not declared in this scope
sample.cpp:275: error: ‘anim’ was not declared in this scope
sample.cpp:277: error: ‘Animation’ is not a class or namespace
sample.cpp:281: error: ‘AnimationTrack’ was not declared in this scope
sample.cpp:281: error: ‘track’ was not declared in this scope
sample.cpp:283: error: ‘KeyFrame’ was not declared in this scope
sample.cpp:283: error: ‘key’ was not declared in this scope
sample.cpp:288: error: expected `;' before ‘animDelay’
sample.cpp:289: error: expected `;' before ‘timOffset’
sample.cpp:292: error: ‘animDelay’ was not declared in this scope
sample.cpp:292: error: ‘timOffset’ was not declared in this scope
sample.cpp:368: error: ‘mAnimState’ was not declared in this scope
sample.cpp:373: error: ‘mBlackOverlay’ was not declared in this scope
sample.cpp:373: error: ‘OverlayManager’ has not been declared
make: *** [all] Error 1

```

---

