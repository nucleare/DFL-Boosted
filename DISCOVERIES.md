# Discoveries

This file simply outlines the discoveries I've made in finding a way of incorporating the use of Incredible to redistribute C/C++ or CPU processes
that are used in DFL to be executed on other machines in a private network with idle CPUs.

## FFMPEG

// Whereas a "RunMe.bat" file runs the following command:

ibconsole /command="ffmpegScript.bat" /openmonitor

// Whereas the "ffmpegScript.bat" file includes

@echo off
set FPATH="C:\Program Files\ffmpeg\bin\ffmpeg.exe"

rem ******************************************************
rem * Clean up output files from previous runs
rem ******************************************************
del /Q .\output*.avi


rem ******************************************************
rem * Convert the input file to 10 various frame sizes
rem ******************************************************
xgsubmit # %FPATH% -i xoreax.wmv -s 100x100 -r 10 output.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 200x200 -r 10 output2.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 300x300 -r 10 output3.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 400x400 -r 10 output4.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 500x500 -r 10 output5.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 600x600 -r 10 output6.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 700x700 -r 10 output7.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 800x800 -r 10 output8.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 900x900 -r 10 output9.avi
xgsubmit # %FPATH% -i xoreax.wmv -s 1000x1000 -r 10 output10.avi

// Whereas "main.py" calls "\mainscripts\VideoEd.pu" which imports ffmpeg
// and is first excuted on line 35 as a job

    job = ffmpeg.input(str(input_file_path))
    
// Then
// Would it be possible to replace the call of ffmpeg with xgsubmit and have ffmpeg run through xgConsole instead of CMD?
// Such as (requires revision) example only and as unverifiedcode

import xgsubmit

job = xgsubmit.(ffmpeg.input(str(input_file_path)))

// needs correction (just a guess)
