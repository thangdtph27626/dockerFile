# Cách thiết kế một Dockerfile

Trong bài viết này, bạn sẽ học cách xây dựng hình ảnh Docker từ đầu, đồng thời triển khai và chạy ứng dụng của mình dưới dạng vùng chứa Docker bằng cách sử dụngDockerfile

##  Dockerfile là gì

Khối xây dựng cơ bản của hình ảnh Docker là mộtDockerfile

A Dockerfilelà một tệp văn bản đơn giản có hướng dẫn và đối số. Docker có thể tự động xây dựng hình ảnh bằng cách đọc hướng dẫn được cung cấp trong tệp Dockerfile.

Trong Dockerfile Mọi thứ bên trái là INSTRUCTION và bên phải là ARGUMENT cho những hướng dẫn đó. Hãy nhớ rằng tên tệp "Dockerfile"không có phần mở rộng.

![image](https://github.com/thangdtph27626/dockerFile/assets/109157942/3694d1a0-9916-4c39-a13c-6fb27d2e5128)

Bảng sau chứa các hướng dẫn Dockerfile quan trọng và giải thích.

<table>
    <thead>
        <tr>
            <th>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Hướng dẫn tập tin Docker</font>
                </font>
            </th>
            <th>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Giải trình</font>
                </font>
            </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">FROM</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Để chỉ định hình ảnh cơ sở có thể được lấy từ sổ đăng ký vùng
                        chứa ( Docker hub, GCR, Quay, ECR, v.v.)</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">RUN</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Thực thi các lệnh trong quá trình xây dựng hình ảnh.</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">ENV</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Đặt các biến môi trường bên trong hình ảnh. </font>
                    <font style="vertical-align: inherit;">Nó sẽ có sẵn trong thời gian xây dựng cũng như trong một vùng
                        chứa đang chạy. </font>
                    <font style="vertical-align: inherit;">Nếu bạn chỉ muốn đặt các biến thời gian xây dựng, hãy sử dụng
                        lệnh ARG.</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">COPY</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Sao chép các tập tin và thư mục cục bộ vào hình ảnh</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">EXPOSE</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;" class="">Chỉ định cổng được hiển thị cho vùng chứa Docker.
                    </font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">ADD</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Đây là phiên bản giàu tính năng hơn của lệnh COPY. </font>
                    <font style="vertical-align: inherit;">Nó cũng cho phép sao chép từ URL là nguồn và </font>
                </font><strong>
                    <font style="vertical-align: inherit;">
                        <font style="vertical-align: inherit;">tự động trích xuất tệp tar</font>
                    </font>
                </strong>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;"> vào hình ảnh. </font>
                    <font style="vertical-align: inherit;">Tuy nhiên, nên sử dụng lệnh COPY thay vì ADD. </font>
                    <font style="vertical-align: inherit;">Nếu bạn muốn tải xuống các tệp từ xa, hãy sử dụng Curl hoặc
                        sử dụng RUN.</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">WORKDIR</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Đặt thư mục làm việc hiện tại. </font>
                    <font style="vertical-align: inherit;">Bạn có thể sử dụng lại hướng dẫn này trong Dockerfile để đặt
                        một thư mục làm việc khác. </font>
                    <font style="vertical-align: inherit;">Nếu bạn đặt WORKDIR, các lệnh như </font>
                </font><code>RUN</code>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">,&nbsp; </font>
                    <font style="vertical-align: inherit;">,&nbsp; </font>
                    <font style="vertical-align: inherit;">, hoặc&nbsp; sẽ được thực </font>
                </font><code>CMD</code>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">thi&nbsp; </font>
                    <font style="vertical-align: inherit;">trong thư mục đó.</font>
                </font><code>ADD</code>
                <font style="vertical-align: inherit;"></font><code>COPY</code>
                <font style="vertical-align: inherit;"></font><code>ENTRYPOINT</code>
                <font style="vertical-align: inherit;"></font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">VOLUME</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Nó được sử dụng để tạo hoặc gắn âm lượng vào vùng chứa Docker
                    </font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">USER</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Đặt tên người dùng và UID khi chạy vùng chứa. </font>
                    <font style="vertical-align: inherit;">Bạn có thể sử dụng hướng dẫn này để đặt người dùng không phải
                        root của vùng chứa.</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">LABEL</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Nó được sử dụng để chỉ định thông tin siêu dữ liệu của hình
                        ảnh Docker</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">ARG</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Được sử dụng để đặt các biến thời gian xây dựng với khóa và
                        giá trị. </font>
                    <font style="vertical-align: inherit;">các biến ARG sẽ không khả dụng khi vùng chứa đang chạy.
                    </font>
                    <font style="vertical-align: inherit;">Nếu bạn muốn duy trì một biến trên vùng chứa đang chạy, hãy
                        sử dụng ENV.</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">CMD</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Nó được sử dụng để thực thi một lệnh trong một container đang
                        chạy. </font>
                    <font style="vertical-align: inherit;">Chỉ có thể có một CMD, nếu có nhiều CMD ở đó thì nó chỉ áp
                        dụng cho cái cuối cùng. </font>
                    <font style="vertical-align: inherit;">Nó </font>
                </font><strong>
                    <font style="vertical-align: inherit;">
                        <font style="vertical-align: inherit;">có thể được ghi đè</font>
                    </font>
                </strong>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;"> từ Docker CLI.</font>
                </font>
            </td>
        </tr>
        <tr>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">ENTRYPOINT</font>
                </font>
            </td>
            <td>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">Chỉ định các lệnh sẽ thực thi khi vùng chứa Docker khởi động.
                    </font>
                    <font style="vertical-align: inherit;">Nếu bạn không chỉ định bất kỳ ĐIỂM NHẬP nào, nó sẽ mặc định
                        là </font>
                </font><code>/bin/sh -c</code>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">. </font>
                    <font style="vertical-align: inherit;">Bạn cũng có thể </font>
                </font><strong>
                    <font style="vertical-align: inherit;">
                        <font style="vertical-align: inherit;">ghi đè ENTRYPOINT</font>
                    </font>
                </strong>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;"> bằng </font>
                </font><code>--entrypoint </code>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;">cờ bằng CLI. </font>
                    <font style="vertical-align: inherit;">Vui lòng tham khảo </font>
                </font><a href="https://devopscube.com/run-scripts-docker-arguments/" data-type="URL"
                    data-id="https://devopscube.com/run-scripts-docker-arguments/">
                    <font style="vertical-align: inherit;">
                        <font style="vertical-align: inherit;">CMD và ENTRYPOINT</font>
                    </font>
                </a>
                <font style="vertical-align: inherit;">
                    <font style="vertical-align: inherit;"> để biết thêm thông tin.</font>
                </font>
            </td>
        </tr>
    </tbody>
</table>

## Xây dựng hình ảnh Docker bằng Dockerfile
Trong phần này, bạn sẽ học cách xây dựng hình ảnh docker bằng ví dụ thực tế. Chúng tôi sẽ tạo hình ảnh docker Nginx từ đầu bằng trang chỉ mục tùy chỉnh.

![image](https://github.com/thangdtph27626/dockerFile/assets/109157942/a83d6b89-645a-44dd-b524-6b88eaefe8ac)

thực hiện theo các bước dưới đây để xây dựng hình ảnh docker.


### Bước 1: Tạo một project Spring boot 

### Bước 2: Tạo DockerFile

```
FROM openjdk:17-jdk-alpine
VOLUME /tmp
ARG JAR_FILE
COPY ${JAR_FILE} app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app.jar"]
```

Bạn có thể chuyển vào JAR_FILE vào một phần của dockerlệnh (nó khác với Maven và Gradle). Đối với Maven, lệnh sau hoạt động:

> docker build --build-arg JAR_FILE=target/*.jar -t myorg/myapp .

Đối với Gradle, lệnh sau hoạt động:

> docker build --build-arg JAR_FILE=build/libs/*.jar -t myorg/myapp .

hoặc bạn có thể tìm hiểu cách build file jar tại [https://www.jetbrains.com/idea/guide/tutorials/hello-world/packaging-the-application/](https://www.jetbrains.com/idea/guide/tutorials/hello-world/packaging-the-application/)

Khi bạn đã chọn hệ thống xây dựng, bạn không cần tệp ARG. Bạn có thể mã hóa cứng vị trí JAR. Đối với Maven, điều đó sẽ như sau:

Dockerfile

FROM eclipse-temurin:17-jdk-alpine
VOLUME /tmp
COPY target/*.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
Sau đó, chúng ta có thể xây dựng một hình ảnh bằng lệnh sau:

> docker build -t myorg/myapp .

## Bước 3: Chạy 
Sau đó chúng ta có thể chạy nó bằng cách chạy lệnh sau:

> docker run -p 8080:8080 myorg/myapp

Nếu bạn muốn khám phá bên trong hình ảnh, bạn có thể mở shell trong đó bằng cách chạy lệnh sau (lưu ý rằng hình ảnh cơ sở không có bash):

> docker run -ti --entrypoint /bin/sh myorg/myapp


```
/ # ls
app.jar  dev      home     media    proc     run      srv      tmp      var
bin      etc      lib      mnt      root     sbin     sys      usr
/ #
``

Nếu bạn có một container đang chạy và muốn xem qua nó, bạn có thể làm như vậy bằng cách chạy docker exec:

``
docker run --name myapp -ti --entrypoint /bin/sh myorg/myapp
docker exec -ti myapp /bin/sh
/ #
``

