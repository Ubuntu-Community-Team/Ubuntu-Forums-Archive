---
title: "C++ com Gstreamer rtp"
date: 2013-01-03
forum: Programming Talk
---

### Post by Goett on 2013-01-03
Estou trabalhando com c++ e qt a pouco tempo e ainda tenho muitas dificuldades, o meu erro se refere a parte do programa em que eu quero captar o video por rtsp, mas na hora de adicionar o bin no pipeline ele sempre da o seguinte erro:  
 
```

 (STM:2846): GStreamer-WARNING **: Name 'srcBin' is not unique in bin 'pipeline3', not adding
 

 (STM:2846): GStreamer-WARNING **: Name 'srcBin' is not unique in bin 'pipeline5', not adding
 

 (STM:2846): GStreamer-WARNING **: Name 'srcBin' is not unique in bin 'pipeline7', not adding
 

 (STM:2846): GStreamer-WARNING **: Name 'srcBin' is not unique in bin 'pipeline9', not adding
 

 (STM:2846): GStreamer-WARNING **: Name 'srcBin' is not unique in bin 'pipeline11', not adding
 

 Sao cinco cameras por isso o erro aparece cinco vezes:
 

 Segue o c[odigo:




 void STMVideoWidget::initSourceBin()
 {
 

     video = QGst::ElementFactory::make("rtspsrc");
     if (!video) {
         qFatal("Failed to create video");
     }
     video->setProperty("location", source);
     video->setProperty("latency", 100);
 

     m_pipeline->add(video);
     QGlib::connect(video, "pad-added", this, &STMVideoWidget::onRtspPadAdded);
 

 }
 

 

 void STMVideoWidget::onRtspPadAdded(const QGst::PadPtr &pad)
 {
 

     if (pad->caps()->internalStructure(0)->value("media").toString() == QLatin1String("video")) {
 

         srcBin =  QGst::Bin::create("srcBin");
         if (!srcBin)
         {
             qFatal("Failed to create srcBin");
         }
 

         QGst::ElementPtr depay = QGst::ElementFactory::make("rtph264depay");
         if (!depay)
         {
             qFatal("Failed to create depay");
         }
         srcBin->add(depay);
 

         //QGst::ElementPtr parse = QGst::ElementFactory::make("h264parse");
         //if (!parse) {
         //    qFatal("Failed to create parse");
        //}
         //parse->setProperty("access-unit", true);
         //parse->setProperty("output-format", "sample");
 

         //s/rcBin->add(parse);
         //depay->link(parse);
 

         QGst::ElementPtr decode = QGst::ElementFactory::make("ffdec_h264");
         if (!decode) {
             qFatal("Failed to create decode");
         }
         srcBin->add(decode);
         depay->link(decode);
 

         QGst::ElementPtr colorSpace = QGst::ElementFactory::make("ffmpegcolorspace");
         if (!colorSpace) {
             qFatal("Failed to create colorspace");
         }
         srcBin->add(colorSpace);
         decode->link(colorSpace);
 

 

         QGst::ElementPtr diveOverlay = QGst::ElementFactory::make("textoverlay");
         if (!diveOverlay) {
             qFatal("Failed to create timeOverlay");
         }
         diveOverlay->setProperty("halignment", 2);
         diveOverlay->setProperty("valignment", 2);
         diveOverlay->setProperty("text", tr("Dive: ") + dive->name->toString() + "\n" + tr("Camera: ") + camName);
         diveOverlay->setProperty("shaded-background", true);
         srcBin->add(diveOverlay);
         colorSpace->link(diveOverlay);
 

         QGst::ElementPtr clockOverlay = QGst::ElementFactory::make("clockoverlay");
         if (!clockOverlay) {
             qFatal("Failed to create clock");
         }
         clockOverlay->setProperty("halignment",0);
         clockOverlay->setProperty("valignment",2);
         clockOverlay->setProperty("time-format","%d/%m/%Y %H:%M:%S");
         clockOverlay->setProperty("shaded-background", true);
         srcBin->add(clockOverlay);
 

 

         leftCenter = QGst::ElementFactory::make("textoverlay");
         if (!leftCenter) {
             qFatal("Failed to create timeOverlay");
         }
         leftCenter->setProperty("halignment",0);
         leftCenter->setProperty("valignment",4);
         srcBin->add(leftCenter);
         diveOverlay->link(leftCenter);
 

         diveData = QGst::ElementFactory::make("textoverlay");
         if (!diveData) {
             qFatal("Failed to create timeOverlay");
         }
         //diveData->setProperty("halignment",0);
 

         diveData->setProperty("deltay", 15);
 

         srcBin->add(diveData);
         leftCenter->link(diveData);
 

         centerCenter = QGst::ElementFactory::make("textoverlay");
         if (!centerCenter) {
             qFatal("Failed to create timeOverlay");
         }
         centerCenter->setProperty("valignment",4);
         srcBin->add(centerCenter);
         diveData->link(centerCenter);
 

         centerTop = QGst::ElementFactory::make("textoverlay");
         if (!centerTop) {
             qFatal("Failed to create timeOverlay");
         }
         centerTop->setProperty("valignment",2);
         srcBin->add(centerTop);
         centerCenter->link(centerTop);
 

         centerBottom = QGst::ElementFactory::make("textoverlay");
         if (!centerBottom) {
             qFatal("Failed to create timeOverlay");
         }
 

         srcBin->add(centerBottom);
         centerTop->link(centerBottom);
 

         rightCenter = QGst::ElementFactory::make("textoverlay");
         if (!rightCenter) {
             qFatal("Failed to create timeOverlay");
         }
         rightCenter->setProperty("halignment",2);
         rightCenter->setProperty("valignment",4);
         srcBin->add(rightCenter);
         centerBottom->link(rightCenter);
 

         rightTop = QGst::ElementFactory::make("textoverlay");
         if (!rightTop) {
             qFatal("Failed to create timeOverlay");
         }
         rightTop->setProperty("halignment",2);
         rightTop->setProperty("valignment",2);
         srcBin->add(rightTop);
         rightCenter->link(rightTop);
 

         rightBottom = QGst::ElementFactory::make("textoverlay");
         if (!rightBottom) {
             qFatal("Failed to create timeOverlay");
         }
         rightBottom->setProperty("halignment",2);
 

         srcBin->add(rightBottom);
         rightTop->link(rightBottom);
 

         rightBottom->link(clockOverlay);
         QGst::PadPtr clockSrcPad = clockOverlay->getStaticPad("src");
         if (!clockSrcPad)
         {
             qFatal("Failed to create clockSrcPad");
         }
 

         srcGhostPad = QGst::GhostPad::create(clockSrcPad);
         if (!srcGhostPad)
         {
             qFatal("Failed to create Bin GhostPad");
         }
         srcGhostPad->setActive(TRUE);
         srcBin->addPad(srcGhostPad);
 

         QGst::PadPtr sinkPad = depay->getStaticPad("sink");
         if (!sinkPad) {
             qFatal("Failed to create sinkPad");
         }
 

         QGst::GhostPadPtr binSinkGhostPad = QGst::GhostPad::create(sinkPad);
         if (!binSinkGhostPad) {
             qFatal("Failed to create Bin sink GhostPad");
         }
         binSinkGhostPad->setActive(TRUE);
         srcBin->addPad(binSinkGhostPad);
 

         m_pipeline->add(srcBin);
 

 

         QGst::ElementPtr encoder = QGst::ElementFactory::make(VideoUtils::VideoUtils::getEncoder());
         if (!encoder) {
             qFatal("Failed to create Encoder");
         }
         encoder->setProperty("bitrate", bitRate);
         //encoder->setProperty("speed-preset", 0);
         //encoder->setProperty("level", 3.1);
         //encoder->setProperty("tune", 7);
         //encoder->setProperty("byte-stream", true);
 

         mux = QGst::ElementFactory::make("avimux");
         if (!mux) {
             qFatal("Failed to create mux");
         }
 

         recBin =  QGst::Bin::create("recBin");
         if (!recBin) {
             qFatal("Failed to create srcBin");
         }
         recBin->add(encoder);
 

         sinkGhostPad = QGst::GhostPad::create(encoder->getStaticPad("sink"));
         if (!sinkGhostPad)
         {
             qFatal("Failed to create Bin GhostPad");
         }
 

         QGst::ElementPtr audio = QGst::ElementFactory::make("autoaudiosrc");
         if (!audio) {
             qFatal("Failed to create audio");
         }
         //audio->setProperty("device","hw:0");
 

         recBin->add(audio);
 

         QGst::ElementPtr audioconv = QGst::ElementFactory::make("audioconvert");
         if (!audioconv) {
             qFatal("Failed to create audioconv");
         }
         recBin->add(audioconv);
         audio->link(audioconv);
 

         QGst::ElementPtr audioenc = QGst::ElementFactory::make("ffenc_aac");
         if (!audioenc) {
             qFatal("Failed to create audioenc");
         }
 

         recBin->add(audioenc, mux);
 

         audioconv->link(audioenc);
 

         audioenc->getStaticPad("src")->link(mux->getRequestPad("audio_%d"));
         encoder->getStaticPad("src")->link(mux->getRequestPad("video_%d"));
 

         recBin->addPad(sinkGhostPad);
 

         m_pipeline->add(recBin);
 

         pad->link(binSinkGhostPad);
 

         srcGhostPad->link(splitter->getStaticPad("sink"));
 

         splitter->getRequestPad("src%d")->link(queue->getRequestPad("sink%d"));
         queue->getStaticPad("src0")->link(display_sink->getStaticPad("sink"));
 

         srcBin->syncStateWithParent();
 

     }
 

 }
 

 void STMVideoWidget::stopRec(){
     isSlice = false;
     mux->sendEvent(QGst::EosEvent::create());
 }
 

 void STMVideoWidget::startRec(){
     if(!rec_sink){
         //queue->getStaticPad("src1")->unlink(sinkGhostPad);
         rec_sink = QGst::ElementFactory::make("filesink");
         if (!rec_sink) {
             qFatal("Failed to create FileSink");
         }
         setFileName();
         recBin->add(rec_sink);
         mux->link(rec_sink);
     } else {
         setFileName();
     }
     startVideoDB();
     queue->getStaticPad("src1")->link(sinkGhostPad);
     m_pipeline->setState(QGst::StateReady);
     m_pipeline->setState(QGst::StatePlaying);
 

 }
 

 


``` Na funcao onRtspPadAddedNa como fazer para o RecBin receber o video de srcBin? Eu ainda nao entendo muito bem como funciona.
 Se alguem puder me ajudar eu agradeço mt.

---

### Post by lisati on 2013-01-03
Translation from translate.google.com
Tradução de translate.google.com

> I'm working with C + + and QT for a short time and still have many difficulties, my mistake refers to part of the program that I want to capture the video for rtsp, but when you add the bin in the pipeline he always of the following error:
> n function onRtspPadAddedNa how to get the video RecBin srcBin? I still do not quite understand how it works.
If someone can help me I appreciate mt.

---

