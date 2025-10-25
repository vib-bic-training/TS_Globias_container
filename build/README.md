# Build a new Docker Image
```bash
docker build -t metrics_globias -f Docker .
```
# Run
```bash
docker run -v "$(pwd)/input:/app/image" -v "$(pwd)/output:/app/output" -v "$(pwd)/bin:/app/bin" -v "$(pwd)/output_metrics:/app/output_metrics" metrics_globias python "/app/bin/metrics.py" --image_path "/app/image/604_img.tif" --label_path "/app/output/604_img_mask.tif" --output_dir "app/output_metrics"
```

- `-v  /path/in/host/datatest:/path/in/container/dataset` : use to moun files inside the container so it becomes accessible
- `$(pwd)` : to get the current path
- `python "/app/bin/metrics.py" --image_path "/app/image/604_img.tif" --label_path "/app/output/604_img_mask.tif" --output_dir "app/output_metrics"` : run the python sript `metrics.py` with the parameters for the raw image, label image and the folder to save the measurements.


## Clean

### Delete all containers including its volumes use,

```bash
docker rm -vf $(docker ps -aq)
```

### Delete all the images,
```bash
docker rmi -f $(docker images -aq)
