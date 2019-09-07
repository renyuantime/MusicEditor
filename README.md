# MusicEditor
This file is about the design of my music editor homework.(Yuan Ren)



Interface:                                    IMusic(Interface) 
Operation IMusic supports:                    -void playSimultaneously(IMusic n)
                                              -void playConsecutively(Imusic n);
                                              -void addNote(Note n,int startPosition);
                                              -void remove(Note n, int startPosition);
                                              -void rise(Note n, int startPosition);
                                              -void fall(Note n, int startPosition)

IMusic represents some kind of music, it could be music in western music system or other system



Implementation of IMusic:                     MusicModel(class)

                                                MusicModel
Fields of MusicModels:                          -int size;
                                               -TreeMap<Pitch, TreeMap<Integer,IBeat>>  collections;

Class MusicModel represents a collection of notes that has order for timing  
Pitch is my first key to the map, Integer which is the beat time(position) is my second key, Ibeat 
could be a headbeat (the first beat in a note,which is onSet) or tailbeat(not the first beat, not onSet).



Class: Pitch                                     Pitch
Fields of  Pitch:                               - int octave
                                          -MusicPitch pitch
I used enum to represent  a field, pitch . Also, I used an int to represent octave



Enum：                                         MusicPitch
12 different pitches in wester music system


Class:                                          Note
Fields of Note                               -int duration
                                             -Pitch pitch
Note represents a note with certain pitch and duration








Interface:                                     Ibeat


implementation of I beat:
Class:                                         HeadBeat (the first beat on a note)
Class:                                         TailBeat (note the first beat on a note)
Fields of Beat                                -Pitch pitch
                                              -int position
Represent a beat, it can be a headbeat or a tail beat. Beat has a field pitch that tells which pitch the beat is and  a field int position  that tells what position at the map this beat is.



Conclusion:
I used TreeMap<Pitch, TreeMap<Integer,IBeat>> structure to represents my collection of notes, which is basically  some kind of music. Pitch is my first key, and Integer(Timing) is my second key, with these two keys we can find a beat and play it. The reason why I use this structure is that map is key-value structure, a key can't have two value , which can ensure that given a specific pitch and a specific time I wont get two beat. Also, Treemap  can order its key automatically, so I override hatched and compreTo and related function to use this feature
to help me order my pitch.
Also I used enum to represent 12 pitches, because in western musical system, this rule is unchanged and certain.




Changes:
 I fixed the detail leaking problem from last week,in my model interface, I changed all the parameters to  IMusic .And, in my IMusicView interface, I also used IMusic as parameter. Also, I added fields like, instrument, volume to my Note and HeadBeat class to store the information provided by this assignment, so I can use this information when I need to play a certain note.










