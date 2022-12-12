### Install environment

``` shell
 pip install -r requirements.txt
```

### Data Preprocessing

## Detection
* can refer to run.ipynb
* for example:
 ``` shell
 !python detect.py --weights 'weights/yolov7-e6e_best.pt' --img-size 1280 --source 'custom_data/private_test' --save-txt --name 'private_test_detect' --augment --conf-thres 0.3 --iou-thres 0.4
 ```
 After detection, the predict label is represented by six values `[class, x_center_norm, y_center_norm, width_norm, height_norm, confidence]`, where x_center, y_center, width and height are the normalized coordinates of the center of the bounding box.
 
 <div align="center">
    <a href="./">
        <img src="./figure/performance.png" width="79%"/>
    </a>
</div>
 
## Training
* train custom data
* can refer to run.ipynb
* for example:
``` shell
!python train_aux.py --batch-size 8 --data 'data/custom_data.yaml' --epochs 20 --img 1280 1280 --cfg 'cfg/yolov7-e6e.yaml' --weights 'weights/yolov7-e6e_best.pt' --hyp 'data/hyp.scratch.p6.yaml'
```

### Convert labels
Convert the labels into demanded form, `[class, x_center, y_center, width, height, confidence]` to `[class, x_min, y_min, width, height]`, where x_min and y_min are coordinates of the top-left corner of the bounding box

can refer to restore _label.ipynb
