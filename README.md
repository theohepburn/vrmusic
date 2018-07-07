## Overview 

vrmusic is an musical experiment that was adapted using the files from Inside Music. Using the link below, you can navigate to their original experiment.

Song Exploder Presents: Inside Music is a [WebVR Experiment](https://webvrexperiments.com) that lets you step inside a song, giving you a closer look at how music is made.

Using their existing code and adapting it I aimed to give the listener a new experience to listen to a song. Following their instructions I included my own audio files. The song that I decided to explore was Bruno Mars '24K Magic'. 

## Preparation

In order for vrmusic to function, I needed to follow the instructions that were inside the Inside Music folder. This began with installing the necessary dependencies as well the required libraries. 

These were installed using the Terminal application on a Mac.

Python was the first dependency to be installed. Mac OSX is already bundled with Python but, the current version of Python did not work when trying to run the `split.py` command. Pydub gave me similar problems as it would not run either and kept outputting `'no module named 'pydub'`. 

Following a tutorial with Matt Bellingham, it was suggested that we use homebrew to install or update newer version of Python. [Homebrew](https://brew.sh/) 

> 'is a package manager for OS X that allows a user to easily install software from the larger body of UNIX and open source software on the Mac' (Gerrity, 2016). 

Running the following command: 

`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

in the terminal allowed me to install homebrew which was then used to update [Python](http://docs.python-guide.org/en/latest/starting/install/osx/) and [Pydub](https://github.com/jiaaro/pydub#installation) to their newest available versions, which allowed them to run.

The commands for updating and installing Python3 and pydub:

`brew install python3`

`pip install pydub`

In order to open and save audio files that are not wav files e.g Ogg Vorbis, I needed to install [lib av](https://www.libav.org/), which is one of the dependencies for python. 

Using the terminal and homebrew, I inputted the following code to install libav:

`brew install libav --with-libvorbis --with-sdl --with-theora`

## Stems

With Phyton and Pydub and the dependencies installed and working, I then needed to run the `split.py` command that would split each stem into 30 second segments to, allow the audio to stream easier on the web. 

Before I split the stems, I had to prepare the stems. The instructions stated that this experiment will work better with 7 stems. I was able to get the multitrack session of 24K Magic that had a total of 21 files.  

![screen shot 2018-07-07 at 10 41 15](https://user-images.githubusercontent.com/37668168/42409777-3b94e4e4-81d7-11e8-9bae-615e557602d7.png)

![screen shot 2018-07-05 at 18 23 55](https://user-images.githubusercontent.com/37668168/42338080-99a5029c-8080-11e8-906e-fa03979eb74f.png)

Using Pro Tools 12, I had to re prepare the stems to ensure there was up to 7 WAV files. 

![screen shot 2018-07-07 at 10 30 34](https://user-images.githubusercontent.com/37668168/42409342-eccf82ac-81d0-11e8-99e3-02076eba84e3.png)

![screen shot 2018-07-05 at 18 22 48](https://user-images.githubusercontent.com/37668168/42338038-729fe158-8080-11e8-9ea5-71209bf6167c.png)

Now that I had 7 stems, in the terminal I had to `cd` into the `audio/stems` folder and run the `split.py` command which gave me the following audio files that were split into 7 different segments which would be used to stream the audio for my vrmusic experiment.

![screen shot 2018-07-06 at 13 22 20](https://user-images.githubusercontent.com/37668168/42378673-08a08154-8120-11e8-8925-961aaeb2dda1.png)
![screen shot 2018-07-06 at 13 23 07](https://user-images.githubusercontent.com/37668168/42378672-088a2670-8120-11e8-82de-0f405422d342.png)
![screen shot 2018-07-06 at 13 23 42](https://user-images.githubusercontent.com/37668168/42378671-0871f294-8120-11e8-8a2a-ee0aff304f24.png)
![screen shot 2018-07-06 at 13 24 06](https://user-images.githubusercontent.com/37668168/42378670-085a1d7c-8120-11e8-8957-b190e1c443ad.png)

## Config

config.js, allowed me to change the meta data and the style codes that would display the information of the chosen song. 

This is what the inside music masters example looked like:

![stem_config](https://user-images.githubusercontent.com/37668168/42413774-20a632bc-821f-11e8-81c4-4241b80d39ca.png)


Following the instructions, I changed the variable `trackconfig` to match the details of 24K Magic. The segments was also edited 7 to match the audio files that were split when I ran `split.py` in the terminal.

![screen shot 2018-07-07 at 20 16 25](https://user-images.githubusercontent.com/37668168/42413921-adb725d2-8222-11e8-9286-56cdea6fe21b.png)

The colour codes were also edited to match the splash screen to keep it more cohesive.

![screen shot 2018-07-07 at 20 20 58](https://user-images.githubusercontent.com/37668168/42413948-4fc1d034-8223-11e8-8574-def72f48d626.png)
![screen shot 2018-07-07 at 20 21 53](https://user-images.githubusercontent.com/37668168/42413961-745edb94-8223-11e8-8d96-7614f9927472.png)
![screen shot 2018-07-07 at 20 20 41](https://user-images.githubusercontent.com/37668168/42413950-4fede8a4-8223-11e8-8240-32b777d28c14.png)
![screen shot 2018-07-07 at 20 20 28](https://user-images.githubusercontent.com/37668168/42413951-5002b7ca-8223-11e8-8171-cc76199885c1.png)

I created a new splash screen to, replace the splash screen that was already included inside the folder that was downloaded from Song Exploder.

![thumbnail](https://user-images.githubusercontent.com/37668168/39891269-03bf2382-5495-11e8-8e88-d70a8c5ddaa8.png)

## Webpack

With the correct dependencies, libraries, stems and the config updated. The next step was to compile the source code and run it using `webpack -p` 

![screen shot 2018-07-07 at 21 39 37](https://user-images.githubusercontent.com/37668168/42414513-577a0be2-822e-11e8-90d9-407e90dddc20.png)

However, when I tried running that code I kept getting error messages so, I referred back to the Inside Music [build](https://github.com/googlecreativelab/inside-music#build) instructions and trying running  `npm install` inside the terminal which turned out to not be responsive. The progress bar didn't even move.

![screen shot 2018-07-07 at 22 51 50](https://user-images.githubusercontent.com/37668168/42414927-74e02f90-8238-11e8-980d-352a65c154ba.png)

I then tried to run `npm update npm -g` to try and rectify the problem. However, when I ran the code the result was lots of error messages that explained that I need to check the permissions.

![screen shot 2018-07-07 at 22 55 21](https://user-images.githubusercontent.com/37668168/42414936-d9c39816-8238-11e8-8b93-c2396bb6b1c9.png)

So, I ran the same code again this time as a 'superuser' `sudo npm install` which removed the error messages and was a success.

![screen shot 2018-07-07 at 23 15 54](https://user-images.githubusercontent.com/37668168/42415076-be95c5ac-823b-11e8-879f-f63fa9984d7d.png)

The next step was for me to try and run webpack -p as a the superuser `sudo webpack -p` but, this was unsuccessful. With this project being outside of my comfort zone, I searched Google and spoke to Matt Bellingham neither of which could find a solution to this problem.

![screen shot 2018-07-07 at 23 18 12](https://user-images.githubusercontent.com/37668168/42415087-1441a462-823c-11e8-879b-0b64c6bd2abf.png)

Unfortunately, I was not able to get the code to work as a packaged file online like the WebVR Experiment. Although I was not able to get the code to work, this I enjoyed this assessment as it allowed me to experiment more with coding which is an aspect that it out of my comfort zone.  


## References

Gerrity, D. (2016). What is Homebrew for OS X? - Quora. [online] Quora.com. Available at: https://www.quora.com/What-is-Homebrew-for-OS-X [Accessed 5 Jul. 2018].
