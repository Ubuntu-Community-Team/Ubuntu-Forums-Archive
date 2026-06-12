---
title: "Java -call order?"
date: 2012-03-21
forum: Programming Talk
---

### Post by abraxas334 on 2012-03-21
I am a bit confused as to what gets called when:
I have a class called FrameDataIterator:
[PHP]
 class FrameDataIterator implements Iterator<IVector>
    {
        // current trajectory index
        private int itraj = -1;
        // current frame in reader
        private int iframe = -1;
        // current reader
        private ITrajectoryReader currentReader; //= inputFiles.get(0);

        public FrameDataIterator()
        {
            openNextReader();
            //try
            //{
            //currentReader.open();
            //} catch (IOException e)
            //{
            //    throw (new RuntimeException("IOException during Trajectory iteration: " + e));
            //}
        }

        private void openNextReader()
        {
            
            currentReader = inputFiles.get(itraj + 1);
            System.out.println("In Sequential Trajectory reader, opening the next reader............"+currentReader.getFileName());
            try
            {
                currentReader.open();
            } 
            catch (IOException e)
            {
                throw (new RuntimeException("IOException during Trajectory iteration: " + e));
            }
        }
}[[/PHP]
and I want to get an iterable over this Iterator. I define somthing like this

[PHP]
 public Iterable<IVector> getFrameDataIterable()
    {
        class FrameDataIterable implements Iterable<IVector>
        {

      
            
            @Override
            public Iterator<IVector> iterator()
            {
                return (getFrameDataIterator());
            }
        }

        return (new FrameDataIterable());
    }
[/PHP]
Though this does not call the getFramDatatIterator method and thus does not open my file. How can i get an iterable, where the OpenNextReader() method gets called every time I request a new iterable? Would it be correct to give the FrameDataIterable class a constructor and in this constructor call iterator()?

Thanks for the help?

---

