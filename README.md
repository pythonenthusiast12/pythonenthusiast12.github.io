<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Chocolate Reviews</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f7f7f7;
            color: #333;
        }
        header {
            background-color: #8B4513;
            color: white;
            text-align: center;
            padding: 50px 0;
        }
        header h1 {
            font-size: 3rem;
            margin: 0;
        }
        header p {
            font-size: 1.2rem;
            margin-top: 10px;
        }
        .container {
            width: 80%;
            max-width: 1200px;
            margin: 30px auto;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .review-form {
            background-color: #fff;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        .review-form h2 {
            color: #8B4513;
            font-size: 2rem;
            margin-bottom: 20px;
        }
        .review-form input, .review-form textarea {
            width: 100%;
            padding: 15px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 1rem;
            box-sizing: border-box;
        }
        .review-form button {
            background-color: #8B4513;
            color: white;
            padding: 12px 20px;
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .review-form button:hover {
            background-color: #7A3F10;
        }
        .reviews {
            margin-top: 40px;
        }
        .review {
            background-color: #f9f9f9;
            padding: 20px;
            margin-bottom: 15px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        .review strong {
            color: #8B4513;
            font-size: 1.1rem;
        }
        .review p {
            font-size: 1rem;
            color: #555;
        }
        .review-date {
            font-size: 0.9rem;
            color: #888;
            margin-top: 10px;
        }
        footer {
            text-align: center;
            padding: 20px;
            background-color: #8B4513;
            color: white;
            margin-top: 40px;
        }
    </style>
</head>
<body>

    <header>
        <h1>Chocolate Reviews</h1>
        <p>We'd love to hear what you think about our delicious chocolates!</p>
    </header>

    <div class="container">
        <div class="review-form">
            <h2>Leave a Review</h2>
            <form id="reviewForm">
                <input type="text" id="name" name="name" placeholder="Your Name" required>
                <textarea id="review" name="review" placeholder="Write your review here..." rows="4" required></textarea>
                <button type="submit">Submit Review</button>
            </form>
        </div>

        <div class="reviews" id="reviewsContainer">
            <h2>Latest Reviews</h2>
            <!-- Reviews will be dynamically displayed here -->
        </div>
    </div>

    <footer>
        <p>&copy; 2024 Delicious Chocolate Co. | All Rights Reserved</p>
    </footer>

    <script>
        // Initialize reviews array (in a real-world app, this would come from a database)
        let reviews = [];

        // Handle form submission
        document.getElementById('reviewForm').addEventListener('submit', function(event) {
            event.preventDefault();

            // Get form data
            const name = document.getElementById('name').value;
            const review = document.getElementById('review').value;

            // Add new review to the reviews array
            const newReview = {
                name: name,
                review: review,
                date: new Date().toLocaleDateString()
            };
            reviews.push(newReview);

            // Clear the form fields
            document.getElementById('reviewForm').reset();

            // Update the display with the latest reviews
            displayReviews();
        });

        // Function to display reviews
        function displayReviews() {
            const reviewsContainer = document.getElementById('reviewsContainer');
            reviewsContainer.innerHTML = '<h2>Latest Reviews</h2>';  // Reset existing reviews

            reviews.forEach(function(review) {
                const reviewDiv = document.createElement('div');
                reviewDiv.classList.add('review');
                reviewDiv.innerHTML = `
                    <strong>${review.name}</strong>
                    <p>${review.review}</p>
                    <div class="review-date">Posted on: ${review.date}</div>
                `;
                reviewsContainer.appendChild(reviewDiv);
            });
        }
    </script>

</body>
</html>
