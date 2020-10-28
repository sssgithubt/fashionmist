# fashionmist

1. Model:
```
model = Sequential([
    layers.Conv2D(filters=64, kernel_size=3, padding='same', activation='relu', input_shape=(28,28,1)),
    layers.MaxPooling2D(pool_size=2),

    layers.Conv2D(filters=32, kernel_size=3, padding='same', activation='relu'),
    layers.MaxPooling2D(pool_size=2),

    layers.Flatten(),
    layers.Dense(256, activation='relu'),
    layers.Dense(10, activation='softmax')
])
```
Test accuracy: 0.9379

2. Thử nghiệm: Sử dụng kernel size 2
```
model = Sequential([
    layers.Conv2D(filters=64, kernel_size=2, padding='same', activation='relu', input_shape=(28,28,1)),
    layers.MaxPooling2D(pool_size=2),

    layers.Conv2D(filters=32, kernel_size=2, padding='same', activation='relu'),
    layers.MaxPooling2D(pool_size=2),

    layers.Flatten(),
    layers.Dense(256, activation='relu'),
    layers.Dense(10, activation='softmax')
])
```
Test accuracy: 0.9386, ghi nhận.

3. Thử nghiệm: Sử dụng random zoom preprocessing
```
model = Sequential([
    layers.experimental.preprocessing.RandomZoom(0.1,input_shape=(28,28,1)),
    layers.Conv2D(filters=64, kernel_size=2, padding='same', activation='relu', input_shape=(28,28,1)),
    layers.MaxPooling2D(pool_size=2),

    layers.Conv2D(filters=32, kernel_size=2, padding='same', activation='relu'),
    layers.MaxPooling2D(pool_size=2),
    
    layers.Flatten(),
    layers.Dense(256, activation='relu'),
    layers.Dense(10, activation='softmax')
])
```
Test accuracy: 0.9293, bác bỏ.

4. Thử nghiệm: Sử dụng filter=64 cho cả 2 convolution layer
```
model = Sequential([
    layers.Conv2D(filters=64, kernel_size=2, padding='same', activation='relu', input_shape=(28,28,1)),
    layers.MaxPooling2D(pool_size=2),

    layers.Conv2D(filters=64, kernel_size=2, padding='same', activation='relu'),
    layers.MaxPooling2D(pool_size=2),

    layers.Flatten(),
    layers.Dense(256, activation='relu'),
    layers.Dense(10, activation='softmax')
])
```
Test accuracy: 0.9492, ghi nhận làm mô hình cuối cùng.

