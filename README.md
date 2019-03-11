# Flower-classifier
Helps to classify roses and sunflowers using tensorflow
Requirements:
* Docker toolbox
* Python
* Tensorflow
* Images with labels

Procedure:
The steps to classify the images is:
1. Open Docker Terminal 
2. Press docker login command login with your docker credentials
3. After that run  docker run -it tensorflow/tensorflow:latest-devel to access the latest stable version of tensorflow in docker.
4. To check the current docker container status use docker ps command to get the container id.
5. Now a root directory along with docker container id is generated.
6. After that enter the pip command pip install tensorflow_hub to install tensorflow hub.
7. Now create a folder on desktop with a folder of flowerpics and scripts.
8. The scripts folder must contain the retrain.py and label.py.
9. In the flowerpics folder create two sub folders named as roses and sunflowers and load nearly 700 images of sunflowers and roses separately.
10. After that train the model using python scripts/label_image.py --graph=/retrained_graph.pb --labels=/retrained_labels.txt --input_layer=Placeholder --output_layer=final_result --image=dublin-rose.jpg
11. The above command contains deblin rose which has to be downloaded separately and copied using the command prompt command docker cp dublin-rose.jpg container_ID:/image_classification/dublin-rose.jpg
12. Now train the model using the command python scripts/retrain.py --bottleneck_dir=/bottleneck/ --model_dir=/inception --output_labels=/retrained_labels.txt --output_graph=/retrained_graph.pb --image_dir=flowerpics/.
13. For training the model takes about 30 minutes.
14. finally test the model using python scripts/label_image.py --graph=/retrained_graph.pb --labels=/retrained_labels.txt --input_layer=Placeholder --output_layer=final_result --image=debrose.jpg
15. The output would be something like this:
     roses 0.9965758
     sunflowers 0.0034241548
    Cool our classifier is working now 
