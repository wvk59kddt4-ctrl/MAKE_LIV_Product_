# MAKE_LIV_Product_
from PIL import Image

import matplotlib.pyplot as plt

from matplotlib.backends.backend_pdf import PdfPages

import os

img_path = "/mnt/data/2911101B-2CFC-4372-B6A3-1010B72054FF.jpeg"

img = Image.open(img_path)

# Define approximate crop boxes for each product card

# (x1, y1, x2, y2, name)

cards = [

    (20, 180, 245, 520, "Distort Hoodie - $120"),

    (250, 180, 475, 520, "Skew Tee - $65"),

    (485, 180, 715, 520, "Fracture Cargo - $130"),

    (720, 180, 950, 520, "Liv Venom Set - $110"),

    (955, 180, 1185, 520, "Midnight Motion Set - $100"),

    (1190, 180, 1420, 520, "Broken Angel Set - $115"),

    (20, 525, 245, 865, "No Rules Track Jacket - $140"),

    (250, 525, 475, 865, "No Rules Track Pants - $115"),

    (485, 525, 715, 865, "Signal Cap - $55"),

    (720, 525, 950, 865, "No Rules Track Set - $125"),

    (955, 525, 1185, 865, "Liv Venom Set Pink - $110"),

    (1190, 525, 1420, 865, "Midnight Motion Set BLK - $100"),

    (20, 870, 245, 1210, "Shadow Puffer - $220"),

    (250, 870, 475, 1210, "Liv Beanie - $40"),

    (485, 870, 715, 1210, "Liv Pendant - $80"),

    (720, 870, 950, 1210, "Broken Angel Set BLU - $115"),

    (955, 870, 1185, 1210, "No Rules Track Set BRN - $125"),

    (1190, 870, 1420, 1210, "Liv Duffle Bag - $90"),

]

output_dir = "/mnt/data/make_liv_products"

os.makedirs(output_dir, exist_ok=True)

saved_files = []

for i, (x1, y1, x2, y2, name) in enumerate(cards):

    crop = img.crop((x1, y1, x2, y2))

    filename = f"{i+1:02d}_{name.replace(' ', '_').replace('$','')}.png"

    path = os.path.join(output_dir, filename)

    crop.save(path)

    saved_files.append(path)

# Create PDF catalog

pdf_path = "/mnt/data/MAKE_LIV_Product_Catalog.pdf"

with PdfPages(pdf_path) as pdf:

    for path in saved_files:

        image = Image.open(path)

        fig, ax = plt.subplots(figsize=(5,7))

        ax.imshow(image)

        ax.axis('off')

        plt.tight_layout()

        pdf.savefig(fig)

        plt.close(fig)

print(f"Created {len(saved_files)} individual product images.")

print(f"PDF saved to: {pdf_path}")

<img width="1254" height="1254" alt="0CC18325-B837-497B-BB3A-A2F5F6143371" src="https://github.com/user-attachments/assets/11f1d022-708e-43db-b7f5-5673e1e263d2" />
<img width="1402" height="1122" alt="326C219D-5151-480E-BB9D-454185CC66DE" src="https://github.com/user-attachments/assets/a826ded5-5b10-42c8-943b-e784eca4df27" />
<img width="1536" height="1024" alt="4B36E615-395B-4414-933F-20DED70374ED" src="https://github.com/user-attachments/assets/c7f82ee5-e9d8-4cd8-a02b-807a57e86906" />

