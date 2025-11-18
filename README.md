# EXP 5 : SPEECH RECOGNITION USING SCILAB

## AIM: 

To perform and verify speech recognition using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM : 
```
clc;
clear;
close;

disp("Loading audio files...");

[y1, fs1] = wavread("C:\Users\Admin\Downloads\referrence.wav");
[y2, fs2] = wavread("C:\Users\Admin\Downloads\test.wav");

// Check sampling rates
if fs1 <> fs2 then
    error("Sampling rates must match!");
end

if size(y1,2) == 2 then
    y1 = mean(y1, 2);
end
if size(y2,2) == 2 then
    y2 = mean(y2, 2);
end

n = min(length(y1), length(y2));
y1 = y1(1:n);
y2 = y2(1:n);

dist = sqrt(sum((y1 - y2).^2));

disp("Euclidean distance (reference vs test): " + string(dist));

if dist < 0.5 then
    disp("Matching with reference (same word)");
else
    disp("Not matching with reference (different word)");
end

figure(0);
subplot(2,1,1);
plot(y1);
title("REFERENCE VOICE SIGNAL");
xlabel("Samples");
ylabel("Amplitude");

subplot(2,1,2);
plot(y2);
title("TEST VOICE SIGNAL");
xlabel("Samples");
ylabel("Amplitude");

figure(1);
plot(y1, 'b');
plot(y2, 'r');
title("Original (Blue) vs Test (Red) Signal");
xlabel("Samples");
ylabel("Amplitude");
legend(["Reference", "Test"]);

disp("Waveforms plotted successfully. Close the graph window manually to finish.");
```

## OUTPUT: 

<img width="1919" height="1116" alt="Screenshot 2025-11-18 113828" src="https://github.com/user-attachments/assets/fea48be3-5376-4599-b99f-0574f66d81ba" />
<img width="1917" height="1123" alt="Screenshot 2025-11-18 113841" src="https://github.com/user-attachments/assets/decea740-3e48-404c-9d4d-3b6b3fa970f7" />



## RESULT: 
Thus the speech recognition using SCILAB was performed and verified.
