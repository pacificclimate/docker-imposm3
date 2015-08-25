# docker-imposm3

Docker container with Imposm3

## Usage

Used to import OSM planet files into a PostgreSQL/PostGIS database.

```bash
sudo docker run \
    -v /full/path/to/planet-latest.osm.pbf:/planet.osm.pbf:ro \
    -v /mnt/ramfs:/cache \
    --name imposm \
    pcic/imposm3 \
        import \
        -mapping /go/src/github.com/omniscale/imposm3/example-mapping.json \
        --read /planet.osm.pbf \
        --write \
        -connection postgis://osm_user:osm_pass@db_host:db_port/osm_db \
        -cachedir /cache \
        -overwritecache \
        -optimize -deployproduction -srid 4326
```