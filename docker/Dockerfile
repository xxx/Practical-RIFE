FROM python:3.13-slim-bookworm

# install deps
RUN apt-get update && apt-get -y install \
    bash ffmpeg git

WORKDIR /rife
COPY requirements.txt .
RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt

# setup RIFE
COPY . .
COPY --chmod=755 docker/inference_img docker/inference_img_SR docker/inference_video docker/inference_video_enhance /usr/local/bin

# add pre-trained models
# RIFE models
# download from https://drive.google.com/file/d/1ZKjcbmt1hypiFprJPIKW0Tt0lr_2i7bg/view
#COPY train_log /rife/train_log
# SAFA models
# download from https://drive.google.com/file/d/1OLO9hLV97ZQ4uRV2-aQqgnwhbKMMt6TX/view
#COPY train_log_SAFA /rife/train_log_SAFA

WORKDIR /host
ENTRYPOINT ["/bin/bash"]

ENV NVIDIA_DRIVER_CAPABILITIES=all
