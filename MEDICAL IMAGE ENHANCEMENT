clc;
clear;
close all;

% Select medical image
[file, path] = uigetfile({'medical.png'});
if isequal(file,0)
    disp('No file selected');
else
    img = imread(fullfile(path,file));

    % Convert to grayscale
    if size(img,3) == 3
        gray = rgb2gray(img);
    else
        gray = img;
    end

    % Noise removal (Gaussian filter)
    blur = imgaussfilt(gray,2);

    % Histogram Equalization (NEW)
    hist_eq = histeq(blur);

    % CLAHE enhancement (advanced)
    enhanced = adapthisteq(hist_eq);

    % Image sharpening
    sharpened = imsharpen(enhanced);

    % -------------------------------
    % Histogram Display 
    % -------------------------------
    figure('Name','Histogram Comparison');

    subplot(2,2,1);
    imshow(gray);
    title('Original Image');

    subplot(2,2,2);
    imhist(gray);
    title('Original Histogram');

    subplot(2,2,3);
    imshow(hist_eq);
    title('Histogram Equalized');

    subplot(2,2,4);
    imhist(hist_eq);
    title('Equalized Histogram');

    % -------------------------------
    % Resize images
    % -------------------------------
    gray = imresize(gray,[460 460]);
    enhanced = imresize(enhanced,[460 460]);
    sharpened = imresize(sharpened,[460 460]);

    % Combine images
    comparison = [gray enhanced sharpened];

    % Show final output
    figure('Name','Medical Image Enhancement Comparison');
    imshow(comparison);
    title('ORIGINAL        ENHANCED        SHARPENED');
end
