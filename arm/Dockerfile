FROM wilsonzhou23/android-auto:latest
LABEL MAINTAINER="wilson.hui.zhou@gmail.com"

# add gradle package
USER root
ADD https://services.gradle.org/distributions/gradle-4.4-all.zip  /home/jenkins/.gradle/wrapper/dists/gradle-4.4-all/9br9xq1tocpiv8o6njlyu5op1/
RUN chmod 777 -R /home/jenkins/.gradle/

# install cloc tool
RUN apt-get update && apt-get -y install cloc

# Switch to user
USER jenkins
WORKDIR $HOME/workdir

# Setup Filter Environment
ENV ANDROID_IMAGES_ARM_FILTER   sys-img-armeabi-v7a-android-21,sys-img-armeabi-v7a-android-27,sys-img-armeabi-v7a-android-28,sys-img-armeabi-v7a-android-29

# Update Android SDK packages
RUN (echo y | android update sdk --all --force --no-ui --filter ${ANDROID_IMAGES_ARM_FILTER})
